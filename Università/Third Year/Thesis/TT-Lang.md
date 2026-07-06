___

This is a progressive journey diary / documentation about Tenstorrent and in particular TT-Lang, that I've explored and studied for my internship.

Introduction/Overview of TT-Lang [here](https://docs.tenstorrent.com/tt-lang/tour/index.html). (Github alternative [here](https://github.com/tenstorrent/tt-lang/blob/main/docs/sphinx/tour/index.md))




# Tenstorrent Card Architecture

(insert card architecture showing and explaining how the node/cores work)

Documentation page about the architecture [here](https://github.com/tenstorrent/tt-metal/blob/main/METALIUM_GUIDE.md).

# TT-Lang core concepts

Documentation page for every ttl.function [here](https://docs.tenstorrent.com/tt-lang/specs/TTLangSpecification.html). (Github alternative [here](https://github.com/tenstorrent/tt-lang/blob/main/docs/sphinx/specs/TTLangSpecification.md))

Documentation page for every ttnn.function [here](https://docs.tenstorrent.com/tt-metal/latest/ttnn/ttnn/api.html).

## Operations

(Define what an TTL operation is)

Every TTL __operation__ needs to be declared:
```python
@ttl.operation(grid=grid_type)
```

The grid type defines on what hardware "grid" the operation runs on.

### Operation grid type

During an operation declaration, the grid type can be set to different values:
```python
grid = (1, 1) # Single core
grid = (4, 4) # Fixed 4x4 grid of cores
grid = ("full") # Lets the compiler use the whole available device grid
```

When declaring full size grid, we cannot assume a specific size, and must handle particular math operations explicitely.

(e.g., uneven divisions with ceiling-division + bounds check)

## Kernel and Sub-kernels

After declaring the operation, the kernel function is typically defined, and inside of it, we will need to define nested functions that will be our sub-kernels.

There are three kinds of sub-kernels inside an operation:
- __compute__, which is the arithmetic compute kernel, so it works on matmuls, elementwise math, reductions, broadcasts...
- __datamovement (read)__, which is one of two types of datamovement kernels that move data between the host DRAM and the device on-chip L1 SRAM memory. In particular this one reads data from the host to the device.
- __datamovement (write)__, is the other type of datamovement kernel, specifically defined to write data from the device back to the host.

Only the compute kernel touches the math engine present in the card.

All the sub-kernels run __concurrently__ on the same node (__check if true__), synchronized through shared buffers.

```python
def kernel(arg : arg_type) -> None:

	@ttl.compute()
	def compute():
		pass
		
	@ttl.datamovement()
	def read():
		pass
		
	@ttl.datamovement()
	def write():
		pass
		
	compute()
	read()
	write()
```

## Dataflow Buffers (DFBs)

These are L1 __circular buffers__ that pass data between the datacompute (DM) and compute kernels.

To declare a buffer, the __shape__ and __block_count__ need to be given.

```python
ttl.make_dataflow_buffer_like(tensor, shape=(...), block_count=N)
```

Keep in mind that bigger blocks equals to fewer, larger transfers that equals to usually more efficient, but must fit in L1/DST registers.

### Buffer shape

The shape describes how many tiles fit in one buffer "block", and is defined in __tile units__.

A tile consists of elements:
```python
TILE_SIZE = 32 # One tile = 32x32 elements
```

So:
```python
shape=(4, 4) # A 4x4 tile block per entry
```

The granularity is:
- block -> tile -> elements

### Buffer block count

The block count is how many blocks the buffer holds. So for example, with `block_count=2` we have double-buffering, meaning that DM can fill one block while compute consumes the other.

## Lock on DFB with reserve / wait

Synchronization on DFBs are managed through two primitives, __reserve__ and __wait__.

A producer (compute or DM writing into a DFB) will block unitl a free slot exists, then it will copy some data into it, and exiting the context manager block will __implicitly__ "push" it. (reserve)

A consumer (compute or DM reading from a DFB) will block until a filled slot is ready, and will "pop" it when exiting the context manager block. (wait)

Getting these primitives backwards is going to cause a __deadlock__.

So basically:
- wait() is used to block itself until a filled slot is ready to be read and worked on it.
- reserve() is used to block itself until an empty slot is available to write.

```python
with dfb.reserve() as blk:
	... # write data into it

with dfb.wait() as block:
	... # read and compute on the read data
```

## TTL copy

This function initiates an __async transfer__.

It can be between DRAM and L1, or even between nodes via multicast pipes. (__check if true__)

It returns a __transfer handle__, and the program must call `wait()` on it before using the data, otherwise it will cause lock errors.

```python
transfer_handle = ttl.copy(src, dst)
```

## Block-level Math

Inside the compute sub-kernel, DFB blocks behave like __small tensors__.

(__Explore further tensors before continuing__)

## Multi-node/grid Coordination (Architecture)

Grids contains nodes, and each node computes only its assigned slice of the tensor.

Node indices are derived from `ttl.node()` while iteration ranges with ceiling division + bound check `if row < rows` when the grid doesn't evenly divide the tensor.

To know the grid dimensions use `ttl.grid_size(dims=N)`.

To know a node's own coordinates within the grid use `ttl.node(dims=N)`.

(__Explore why need to specify dims=N__)

## Multicast (Pipe / Pipenet)

(__WTF is pipe/pipenet__)

To share data across nodes without each one re-reading DRAM:
```python
pipe = ttl.Pipe((0,), (slice(1, num_working_nodes),))  # src node -> dst nodes
net = ttl.PipeNet([pipe])
net.if_src(pipe_src_fn)   # runs only on the source node
net.if_dst(pipe_dst_fn)   # runs only on destination nodes
```

Pipes are used heavily to __broadcast__ a shared input to multiple cores instead of redundant DRAM reads.

## GroupTransfer

The `ttl.GroupTransfer` batches multiple `ttl.copy` calls and waits on them together.

Useful when one input fans out to many outputs.

## Printing for debug purposes

Documentation page about it [here](https://docs.tenstorrent.com/tt-lang/reference/print-debugging.html).

To make print calls work inside the sub-kernels, run the program like this:
```bash
TT_METAL_DPRINT_CORES=0,0 python my_script.py
```

If printing the full 32x32 tile contents from the DFB, the tile must be __live__, meaning in between wait/pop ir reserve/push

In compute kernels, guard prints with `thread="math"`, `thread="pack"`, or `thread="unpack"` to avoid overlapping output from the three TRISC threads.