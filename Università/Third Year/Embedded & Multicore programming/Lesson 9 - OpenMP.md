___

OpenMP is an threading interface based on Linux's Pthreads.
(On Windows it will be implemented on top of another threading abstraction)

It can be used to runu code on GPUs.

While OpenMP is implemented using Phtreads, and it can be possible to use both at the same time in a program, it is always better to use either one and not both.

In principle one should avoid running more threads than the number of cores of the machine.

# Thread levels in MPI

`MPI_THREAD_SINGLE`: rank is not allowed to use threads. ( or it has only one thread)

`MPI_THREAD_FUNNELED`: rank can be multi-threaded and can call MPI functions, but the other threads cannot.

`MPI_THREAD_SERIALIZED`: rank can be multi-threaded but only one thread at a time can call MPI functions.

`MPI_THREAD_MULTIPLE`: rank can be multi-threaded and any thread can call MPI functions.
- This threading level is usually not implemented because it is very slow and/or not efficient.

# Time
```c
#include <sys/time.h>

#define GET_TIME(now){
	struct timeval t;
	gettimeofday(&t, NULL);
	
}
```

A block of code is __thread-safe__ if it can be simultaneously executed by multiple threads without causing problems.

The strtok function is __not__ thread-safe because it caches the input line, and this is shared, so multiple simultaneous thread calls can lead to unexpected output.

There exist a thread-safe version of strtok, that is called strtok_r.
This alternative function needs another input that is a pointer to a memory location to save the string.


___

# Lecture 11_11_25

OpenMP's purpose is to decompose sequential programs into __components__ so that these can be executed in parallel.

OpenMP relies on compiler directives (`#pragma`) for decorating portions of code that the compiler will attempt to parallelize.

Programs that uses OpenMP are globally sequential and locally parallel.
These follows the __fork-join__ paradigm, so a program will begin sequentially, and when in need, it will fork into multiple sub-programs.

Compilers that don't support the pragmas will ignore them.

```c
#pragma omp parallel

// parallel code here...

#pragma omp end parallel

```

The set of threads in OpenMP is called a __team__:
- The master is the original thread of execution.
- The master is in many cases, also the parent thread.
- The children are the threads that are started by the parent.

The master thread executes the parallel code too, not only the children.
