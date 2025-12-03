___

32core x 4 = 128 thread

è il massimo numero di threads utilizzabili nel cluster

progetto
una versione usando solo cuda e un'altra versione usando mpi+openMP

___

## Partitioning

Il `default partitioning` assegna blocchi contigui di iterazioni a ogni thread.

The `cyclic partitioning` assigns in a `round robin` way the threads iteration.

When executing a function with __linear cost__ (iteration $n$ will cost linearly more than the first iteration), it's better to use a cyclic partitioning because in this way, the last thread will not get all the last iterations, which are the more costly ones.

## Schedule Clause

asd

### Default schedule

```C
pragma omp parallel for num_threads(thread_count) \
	reduction(+:sum)
```


The type of the schedule can be:
- __Static__, where the iterations can be assigned to the threads __before__ the loop is executed.
- __Dynamic__ or __guided__, where the iterations are assigned to the threads __while__ the loop is executing.
- __Auto__, where the compiler and/or the runtime system determines the schedule.
- __Runtime__, where the schedule is determined at runtime.
And we can define the __chunksize__ (block of iterations) of every thread.
### Static schedule

Using a static schedule we can define for every thread its iterations.

```c
schedule(static,1)

// Thread 0: 0,3,6,9
// Thread 1: 1,4,7,10
// Thread 2: 2,5,8,11
```

### Dynamic schedule

It's recommended to use dynamic scheduling when we doubt that all the iterations won't have the same cost.

The more we increase the chunksize, the more we will probably have threads that work more than others.

So it's better to leave the chunksize at $1$, which will yield a better load balancing, but will also result in a higher overhead due to scheduling the chunks.

### Guided schedule

This type of scheduling assigns bigger chunks at the beginning, where the risks of assigning bigger chunk, resulting in a imbalance of execution for a thread, is small, to gradually assign smaller and smaller chunks when close to the end.

### Runtime schedule

This type lets the user choosen during runtime a schedule type.

### Which one to use

Use:
- Static, if iterations are homogeneous.
- Dynamic or guided, if execution cost varies.

If in doubt, set:
```c
#pragma omp parallel for schedule(runtime)
for(...)
```

There is no guarantee that the auto schedule will select thte most performing schedule option.

So try different options and measure the code.

## Master/Single Directives

Both these directives force the execution of the following structured block by a single thread.

There are differences between the two.

## Barrier Directive

This directive blocks all the threads that reaches this barrier point until all team threads reach the point.

## Section/sections Directives

This is used as a switch clause.

## Ordered Directive (Synchronization Construct)

This directive is used inside a parallel for, to ensure that a block will be executed as if in sequential order.



## Data Dependency Resolution

There are $6$ techniques to resolve data dependecies.

### Reduction/Induction variable fix

When executing a for loop that uses a variable that its updated inside his body,
we have a data dependency that can cause wrong results.

#### Example

The following code snippet may be wrong if the $x$ iteration gets executed before the $y$ iteration, where $x>y$. The `v` variable has a different value than expected because it didn't get updated in the first iteration, that didn't happen before.

```c
double v = start;
double sum = 0;
for (int i=0; i<N; i++){
	sum = sum + func(v);
	v = v + step;
}
```

To fix this, we can refactor the line where `v` gets updated into a __closed formula__:
```c
double v;
douuble sum = 0;
for (int i=0; i< N; i++){
	v = start + i*step;
	sum = sum + func(v);
}
```

Essentially we made the `v` variable calculation __independent__ from the iteration, by multiplying the `step` for `i` times, where `i` is the iteration number.

### Loop Skewing

Another technique involves the rearrangement of the loop body statements.

When executing a for loop that has in its body some code that calculates a value __based on a value__ calculated in the previous iteration.

#### Example

```c
for (int i=1; i<N; i++){
	y[i] = func(x[i-1]);
	x[i] = x[i]+c[i];
}
```

We need to make sure that the statements that consume the calculated values that causes the dependence, use values generated __during the same iteration__.

To do loop skewing, we need to unroll the loop and try to see the repetition patter:
```c
y[1] = func(x[0]);
x[1] = x[1]+c[1]; // This
y[2] = func(x[1]); // and this
x[2] = x[2]+c[2];
…
y[N-2] = func(x[N-3]);
x[N-2] = x[N-2]+ c[N-2]; // This
y[N-1] = func(x[N-2]); // and this
x[N-1] = x[N-1]+ c[N-1]
```

### Partial Parallelization

```c
// Snippet of not parallelizable code represented below

for (int i=1; i<N; i++){
	for (int j=1; j<M; j++){
		data[i][j] = data[i-1][j] + data[i-1][j-1];
	}
}
```

In this case we use a ISDG, or Iteration Space Dependency Graph.

A ISDG is made up of nodes that represent a single execution of the loop body, and edges that represent dependencies.

![|500](ISDG_image_from_PMC14.pdf_at_page_63)

If a node $x$ doesn't possess any edges that goes onto another node $y$, then these two nodes are parallelizable.

This technique is best used when there are $2$ or more index.

### Refactoring

Refactoring is a technique that rewrites the loop(s) so that parallelism can be exposed.

![|500](ISDG_image_from_PMC14.pdf_at_page_64)

In this case, we need to make the iteration of the nodes execute __diagonally__.
By doing this the nodes on the next iteration are parallelizable.

### Fissioning

Fissioning means breaking the loop apart into a sequential and a parallelizable part.

#### Example

```c
s = b[0];
for (int i=1; i<N; i++){
	a[i] = a[i] + a[i-1]; // This line is not parallelizable
	s = s + b[i]; // This one is parallelizable
}
```

So to make parallelizable this for loop we divide the body into $2$ for loops, one sequential and one parallel:

```c
// Sequential part
for (int i=1; i<N; i++){
	a[i] = a[i] + a[i-1];
}

// Parallel part
s = b[0];
#pragma omp parallel for reduction(+ : s)
for (int i=1; i<N; i++){
	s = s + b[i];
}
```

### Algorithm Change

If everything else fails, switching the algorithm may be the answer.

#### Example

The Fibonacci sequence can be calculated with:
```c
for (int i=2; i<N; i++){
	int x = F[i-2];
	int y = F[i-1];
	F[i] = x + y;
}
```

It can be parallelizable via Binet's formula.

## Output Dependence Removal (WAW)

To guarantee that at the end of the execution the computed variable $x$ is the one computed in the last iteration of a loop, openMP defines a `lastprivate` directive.

```c
#pragma omp parallel for shared(a,c) lastprivate(d)
for (int i=0; i<N; i++){
	y[i] = a * x[i] + c;
	d = funcABS(y[i]); // The WAW dependency is on this d variable
}
```


sinfo
squeue
salloc -N 4 --ntasks-per-node=32 per prenotare un job

exit oppure ctrl+D per rilasciare il job

il numero di nodi + tempo richiesto influenzano l'attesa richiesta per i nodi

salloc -N 4 --ntasks-per-node=32 --time=00:10:00

srun  -n 1 ./programma_compilato per runnare 1 processo di programma_compilato

___
ignorare guida mpi sul sito e fare

source /home/guest/openmpi-4.1.6/init.sh
export LD_LIBRARY_PATH=/home/guest/
mpicc pi_parallel.c -o pi_parallel
mpirun --mca pml ucx --mca btl ^openib -x LD_LIBRARY_PATH pi_parallel

___

salloc -N 1 --ntasks-per-node=1 --gpus=1

source /home/guest/cuda-12.8/init.sh

nvcc test_cuda.cu -o test_cuda

nvcc -arch=sm_75 test_cuda.cu -o test_cuda

NON fare ./test_cuda (perché stai sul submitter), fare invece 
srun -n 1 ./test_cuda

___

scp -r work desensi@192.168.1.102:./
oppure fare con git per trasferire file


___

```bash
#!/bin/bash
#SBATCH -N 2
#SBATCH --tasks-per-node=32
#SBATCH --gpus=2

```
sbatch sbatch.sbatch

scontrol show job 676767

cat slurm-676767.out

Per fare test di prestazioni etc usare modalità sbatch

invece per fare debug meglio usare modalità interattiva

___

salloc -N 2 --ntasks-per-node=32 --exclusive

per far girare in modo esclusivo il programma.

