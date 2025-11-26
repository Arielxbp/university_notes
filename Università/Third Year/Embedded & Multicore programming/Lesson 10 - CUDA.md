___

CUDA is NVIDIA's parallel computing architecture and framework.

Control units inside a GPU are far less than those inside a CPU, so in a GPU we __don't__ have:
- Branch prediction.
- Out-of-order execution.

The latency required to access the DRAM is high but it has a high throughput.

So applications that need __low latency__ are executed by the CPU, while those that need __high throughput__ are done by the GPU.

## Architecture of a CUDA-capable GPU

We have a set of cores, called streaming processors, a block of cores is called SM. (Streaming multiprocessor)
Two or more SMs form a __building block__.

## Use-cases for CPU/CPU

CPUs are better for sequential parts where latency matters.

GPUs are better for parallel parts where throughput matters.

## CPU-GPU Architecture

Because the GPU has his own RAM, distinct from the systems RAM.
We need to send the data from the RAM to the VRAM, once finished manipulating that data we need to retrieve said data from the VRAM and send it back to the RAM.

In modern version of CUDA this transfer is transparent, so we don't notice it, but this transfer impacts efficiency not in a trascurable way.

## Writing programs with CUDA

There must be a specified function that is going to be executed by all the threads.
This function is called __kernel__.

Also we need to specify how threads are __arranged__ in the grid/blocks.

CUDA organizes the threads in a $6-D$ structure. (while also lower dimensions are possible)

Each thread has a position in a $1D$, $2D$ or $3D$ block and each block has a position in a $1D$, $2D$ or $3D$ grid.

Each thread is aware of its position in the overall structure.

## Function decorations

- `__global__`  can be called from the host or the GPU and executed on the device/GPU.

- `__device__` is a function that runs on the GPU and can only be called from within a kernel, so only from the GPU.

- `__host__` is a function that can only run on the host.

## Thread position in the grid/block

Threads are arranged in a $6D$ space.

There are a few ways to know the position of a thread:

- `blockDim` contains the size of each block.

- `gridDim` contains the size of the grind, in blocks.

- `threadIdx` is the $(x,y,z)$ position of the thread within a block.

- `blockIdx` is the $(b_{x}, b_{y}, b_{z})$ position of a thread's block within the grid.


__DOMANDA ESAME__: saper calcolare l'unique thread id di un thread.
(fino a $2$ dimensioni)

## Thread Scheduling

Each thread runs on a streaming processor (CUDA core).

Sets of cores on the same SM share the control unit, so they must synchronously execute the same instruction.

Different SMs can run different kernels.

Each block runs on an SM.

Once a block is fully executed, the SM will run the next one.

Not all the threads in a block run concurrently.

Scheduling threads is basically free.

## Warps

Consecutive threads in a block are executed in groups called __warps__.

Every $32$ consecutive threads are grouped into warps.

Every thread inside the same warp must do the same instruction.

Different warps can do different instructions.

### Warp Divergence

There can be instances where inside a warp there is a divergence in the executed instructions caused by conditional operations.

In these cases the threads that evaluate to true for the conditional will execute the conditional's block, while the threads that didn't will be stalled.
When the threads will finish the conditional's block they will be stalled and the other threads will evaluate the `else` block.

### Context Switching

Usually a SM has more __resident__ blocks/warps than it is able to concurrently run.
This is not a problem because it can switch seamlessly between them.

Each thread has its own execution context that is maintained __on-chip__, meaning that the context switch is basically free.

If an instruction to be executed by a warp needs to wait for the output of a previously initiated __long-latency__ operation, said warp is not selected for execution and instead, another resident warp that is no longer waiting for results will be selected for execution.
(This switching is called __latency tolerance__)

This ability to tolerate long-latency operations is the main reason GPUs do not dedicate nearly as much chip area to cache memories and branch prediction mechanisms as do CPUs.

## Examples

The dimension of the block should be a multiple of 2 because in this way, it will line up with multiples of 32, which is the size of a warp.

### Example $1$

A CUDA device allows up to $8$ blocks and $1024$ threads per SM, and $512$ threads per block.

For 8x8 blocks we would have 64 threads per block, and to fill all the 1024 threads of the SM we would need 1024/64=16 blocks.
However the device can have at most 8 blocks, thus we would end with only 64x8=512 threads per SM, so we are not utilizing fully the resources.
This may cause the scheduler to not find threads to schedule when some thread is waiting for long-latency operations.

## Memory Types

There are multiple types of memories, some are __on-chip__ and some __off-chip__.

Each SM has its own shared memory, but it can't use other SMs shared memory.

The only part accessible by the host (CPU) through CUDA functions is the __global memory__.

In the kernel function there are differences between types of data.
Variables that are not arrays goes into __registers__.
Arrays allocated in the stack goes into the global memory and not in the register.
Shared memory variables are visible only to a single block.

### Registers

There are as much registers as there are threads.
Registers on a core are split among the resident threads.

This is the reason behind the free context switch:
- Because the switched in threads have their registers already ready to work.

The compute capability determines the maximum number of registers that can be used per thread

The number of maximum registers per thread influences the maximum number of resident threads we can have on an SM.
- We can use only the registers and not overflow into the shared memory to not slow down but the number of threads active will be lower.
- We can use all the threads but this will cause some accesses to the shared memory cause all of the registers will be full.

The __occupancy__ is the ratio of resident warps over the maximum possible resident warps.
- A value of occupancy close to $1$ is optimal.
This value can be analyzed through a __profiler__.

Generally to increase occupancy:
- We need to reduce the number of registers required by the kernel.
	- E.g. by avoiding to have too many temporary variables.
- Use a GPU with a higher register per thread limits.

