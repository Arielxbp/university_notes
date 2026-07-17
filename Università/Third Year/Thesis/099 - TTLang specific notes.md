___

This is a progressive journey diary / documentation about Tenstorrent and in particular TT-Lang, that I've explored and studied for my internship.

Introduction/Overview of TT-Lang [here](https://docs.tenstorrent.com/tt-lang/tour/index.html). (Github alternative [here](https://github.com/tenstorrent/tt-lang/blob/main/docs/sphinx/tour/index.md))

# bash exports

```bash
export TT_METAL_LOGGER_LEVEL=FATAL # Set the logger level to FATAL to reduce log output

export TT_METAL_DPRINT_CORES=0,0 # Set the specific core to capture print statements
```

# Tenstorrent Card Architecture

Documentation page about the architecture [here](https://github.com/tenstorrent/tt-metal/blob/main/METALIUM_GUIDE.md).

## Architecture Overview

Tenstorrent chips are a __grid__ of different nodes, where most are compute nodes called a __Tensix core__. Other nodes are for memory, chip management and ethernet.

The overall chip is then called a __Tensix processor__.

The following image shows the grid of a Tenstorrent processor, where:
- D = DRAM
- T = Tensix core
- E = Ethernet
- A = ARC/Management
- P = PCIe

![|350](https://github.com/tenstorrent/tt-metal/raw/main/docs/source/common/images/tenstorrent-wormhole-logical-noc-diagram.webp)

## Tensix core

Each Tensix contains $5$ RISC-V CPUs, each with a different function:
- Data Movement $0$ and Data Movement $1$.
- Unpack, math and pack.

They also contain $2$ NoC interfaces, a vecotr unit (SFPU), a matrix unit (FPU) and a pack and unpacker, as well as $1.5$ MB of SRAM (called L1 in the architecture) to hold transient data and to facilitate data exchange between local components.

### RISC-V cores

The RISC-V cores in Tensix primarily handle __instruction dispatching__ and __control flow__. They issue commands to the NoC/Matrix/Vector/Packer/Unpacker units, which in turn perform the actual computational work, rather than executing the computations directly.

So the RISC-V cores do not compute, they instead issue commands to the other units.

This specific design of the cores separates control flow and data movement from the raw computation, providing various advantages:
- __Uninterrupted Compute Throughput__, by decoupling data movement from computation, the specialized compute units are __never interrupted__ by data handling or control logic.
- Asynchronous execution, since each RISC-V core operates independently, it enables efficient __producer-consumer__ pipelining. (e.g., DM core $0$ can asynchronously fetch the next batch of data from memory while the math core dispatches compute instructions for the current batch, and the DM core $1$ saves the previous batch's results)
	- This overlapping hides memory latency without requiring complex hardware schedulers.
- Predictability and determinism, the Tenstorrent architecture omits hardware-managed cache hierarchies and dynamic thread scheduling. Instead, it preferres executing explicit, statically-scheduled instructions to move data and dispatch compute.

![|600](https://github.com/tenstorrent/tt-metal/raw/main/docs/source/common/images/tenstorrent-tensix-rough-block-diagram.webp)

So the data flow is:
- NoC $0$ reads data from DRAM (or accept data from other Tensixes).
- Unpacker unpacks the data into a format that can be processed by the vector/matrix unit.
- Vector/matrix unit performs the computation.
- Packer packs the result back into a format for storage.
- NoC 1 sends the result to DRAM (or other Tensixes).

### Data flow between Tensix with NoCs

The Network-on-Chips (NoCs) present in each Tensix operate in a "quasi-full-duplex" mode, so the two NoCs traverse the chip in __opposite directions__. This bidirectional capability allows both NoCs to __simultaneously__ send and receive data.

The $2D$ torus topology design used for the chip ensures __full connectivity__, enabling any Tensix on the chip to communicate with any other Tensix.

While the opposing directional flow of the two NoCs naturally provides efficient return paths for data, regardless of the originating location.

For complex operations and data transfers, the RISC-V cores can utilize both NoCs for the same data movement simultaneously, __doubling the effective bandwidth__ at the cost of not being able to overlap reads and writes. It this case, SRAM can be used as a temporary storage for intermediate results within the operation itself.
 
### SRAM (Static RAM) and Circular Buffers

The SRAM stores data local to the Tensix and feeds the compute engines/peripherals.

The three sub-kernels, reader, compute and writer, coordinate their execution using __circular buffers__, which are implemented in SRAM and facilitated by hardware synchronization.

These buffers act as producer-consumer __queues__, enabling safe and efficient data exchange between sub-kernels.

Each sub-kernel interacts with the buffers as follows:
- Reader kernel: Writes data into the circular buffer and signals when new data is available.
- Compute kernel: Waits for data to become available in the buffer before processing it. After computation, it writes the results to another buffer and marks them as ready.
- Writer kernel: Waits for the computed results to appear in the buffer before writing them to the output location.

This mechanism ensures that each sub-kernel only proceeds when the necessary data is ready, preventing race conditions and enabling asynchronous, pipelined execution across the hardware.

Tenstorrent's hybrid approach allows data to reside in either SRAM or DRAM as needed. In traditional architectures, intermediate tensors that exceed cache capacity get evicted to DRAM, or context switches invalidate cache contents, creating performance bottlenecks.

When operations can access data stored locally within the same Tensix, NoC bandwidth requirements are eliminated entirely, further improving performance.

#### SRAM as globally addressable memory

Tenstorrent's architecture treats the $1.5$ MB of local SRAM inside each Tensix core as explicitly globally addressable memory.

Cross-core SRAM communication is handled through the NoCs.

This design enables advanced performance optimizations like __NoC multicasting__, so rather than every core independently reading the same input data from DRAM, a dedicated core can read the data once and __broadcast__ it directly to the SRAM of all the other cores.

## Tiles

Tenstorrent hardware operates natively on $32\times32$ element tiles.

A tile is the basic unit of both data layout and compute:
- A $32\times32$ grid of elements, all sharing the same data type.

The matrix unit (FPU) treats one tile as __a single operand__, it doesn't do scalar-by-scalar operations, rather it issues one instruction sequence that turns two $32\times32$ tiles into a single $32\times32$ result tile.

So data is processed in $32\times32$ blocks, and Tensix cores perform matrix operations on one or more of these tiles.

### Faces

A tile is __subdivided__ into four $16\times16$ faces, each stored as a __contiguous block in memory__, arranged sequentially to give efficient access patterns for the compute units.

This subdivision is done to benefit the hardware, because it maps cleanly to the fixed-width of the internal registers used by the compute engines. So the reason for using faces is that the matrix engine natively multiplies 16x16 matrices, and tile multiplication is decomposed into multiple face multiplications.

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

Do not invoke the sub-kernels explicitly.

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