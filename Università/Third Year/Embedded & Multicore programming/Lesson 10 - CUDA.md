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

Threads in a block are executed in groups called __warps__.

Every $32$ threads are grouped into warps.

Every thread inside the same warp must do the same instruction.

Different warps can do different instructions.

### Warp Divergence

There can be instances where inside a warp there is a divergence in the executed instructions caused by conditional operations.

In these cases the threads that evaluate to true for the conditional will execute the conditional's block, while the threads that didn't will be stuck.
When the threads will finish the conditional's block they will be stuck and the other threads will evaluate the `else` block.
