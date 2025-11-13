___

Lesson 2 and 3 were a recap of C language.

# Introduction

Generally __serial__ programs don't benefit from multiple cores.

There exists compilers that transform serial code into parallel code, but it's still not good enough.

We will write explicit parallel programs using C language and four libraries:
- MPI. (Message-Passing Interface)
- PThreads. (Posix Threads)
- OpenMP.
- CUDA.

There exist higher-level libraries, but they trade-off ease-of-use for performance.

# Types of parallel systems

There are two types of parallel system:
- Shared-memory ones.
	- In this type of system, all cores can share access to the computer's memory, so they can coordinate themselves by looking and updating the shared memory locations.
- Distributed-memory ones.
	- In this type of system, each core have its own private memory.
	- So every ore must communicate explicitly with other cores by sending messages across a network.

There are two types of parallel system's architecture:
- MIMD (Multiple-Instruction Multiple-Data).
	- Each core has its own control units and can work independently from the others.
- SIMD (Single-Instruction Multiple-Data).
	- All cores share the control units, meaning that they must all execute the same instruction, otherwise they all stay idle.
	- Theoretically every core could be working on different instructions, but this can lead to a situation where, one core is adding bits, where a second one is in idle, but then the first one goes idle, and now the second one starts to work on those bits.

# Concurrent/Parallel/Distributed Systems

A concurrent system can work on multiple tasks at any time.

A parallel system can have multiple tasks going, but these need to be cooperating closely.

A distributed system can have multiple tasks going, and these are more loosely coupled than the parallel systems.

# von Neumann architecture

Il modello di von Neumann usa solamente dati nei registri e nella ram.

Quindi la CPU ha bisogno di leggere (ricavare) dati dalla memoria, o scrivere dati nella memoria.

La separazione tra la CPU e la RAM è chiamato il bottleneck di von Neumann, in quanto il bottleneck è questa latenza presente quando si leggono dati.

# MPI

## Comunicatore

È un gruppo di processi che possono comunicare fra di loro.
Questo gruppo viene creato quando viene eseguito `MPI_Init`.

È usato per partizionare più processi in modo da usarli con più modularità.

Uno stesso processo può avere diversi identificatori in comunicatori diversi.

Rank sta per l'ID del processo.

