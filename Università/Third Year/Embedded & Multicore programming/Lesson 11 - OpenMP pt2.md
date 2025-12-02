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

The following code snippet may be wrong if the second iteration gets executed before the first iteration, the `v` variable has a different value than expected because it didn't get updated in the first iteration, that didn't happen before.

```c
double v = start;
double sum = 0;
for (int i=0; i<N; i++){
	sum = sum + func(v);
	v = v + step;
}
```

To fix this, we can write the line where `v` gets updated into a __closed formula__:
```c
double v;
douuble sum = 0;
for (int i=0; i< N; i++){
	v = start + i*step;
	sum = sum + func(v);
}
```

