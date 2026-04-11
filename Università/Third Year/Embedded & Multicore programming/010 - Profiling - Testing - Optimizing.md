___

## Cluster's Benchmarks result

Doing tests type 7 designed for benchmarking optimization improvements:

### Sequential results

Time: 111.221132
Result: 507805 12177.071289 400548 23157.615234 511786 34230.769531 511786 44824.339844

Time: 111.201311
Result: 507805 12177.071289 400548 23157.615234 511786 34230.769531 511786 44824.339844

Time: 111.118974
Result: 507805 12177.071289 400548 23157.615234 511786 34230.769531 511786 44824.339844

Time: 111.185320
Result: 507805 12177.071289 400548 23157.615234 511786 34230.769531 511786 44824.339844

Time: 111.265753
Result: 507805 12177.071289 400548 23157.615234 511786 34230.769531 511786 44824.339844

### Cuda results

Using test_files07 (made for benchmarking optimization)

__With blocksize=32__
Run   1: 0.091909 s
  Run   2: 0.087486 s
  Run   3: 0.086986 s
  Run   4: 0.087003 s
  Run   5: 0.087002 s

========================================
  Monte Carlo timing summary (1000 runs)
========================================
  Mean     : 0.087331 s
  Std dev  : 0.000681 s
  Median   : 0.086997 s
  Min      : 0.086907 s
  Max      : 0.091909 s
  95% CI   : [ 0.087289 , 0.087373 ] s
  CV       : 0.78 %
========================================

All runs produced consistent results.

Result (from warm-up run): 507805 12177.071289 400548 23157.615234 511786 34230.769531 511786 44824.339844

__With blocksize=64__
Run   1: 0.077469 s
  Run   2: 0.071780 s
  Run   3: 0.071282 s
  Run   4: 0.070848 s
  Run   5: 0.070821 s

========================================
  Monte Carlo timing summary (1000 runs)
========================================
  Mean     : 0.072823 s
  Std dev  : 0.000918 s
  Median   : 0.072818 s
  Min      : 0.070537 s
  Max      : 0.077469 s
  95% CI   : [ 0.072766 , 0.072879 ] s
  CV       : 1.26 %
========================================

All runs produced consistent results.

Result (from warm-up run): 507805 12177.071289 400548 23157.615234 511786 34230.769531 511786 44824.339844

__With blocksize=128__
Run   1: 0.089481 s
  Run   2: 0.076528 s
  Run   3: 0.071077 s
  Run   4: 0.070082 s
  Run   5: 0.070099 s

========================================
  Monte Carlo timing summary (1000 runs)
========================================
  Mean     : 0.072505 s
  Std dev  : 0.001110 s
  Median   : 0.072575 s
  Min      : 0.070067 s
  Max      : 0.089481 s
  95% CI   : [ 0.072436 , 0.072574 ] s
  CV       : 1.53 %
========================================

All runs produced consistent results.

Result (from warm-up run): 507805 12177.071289 400548 23157.615234 511786 34230.769531 511786 44824.339844

__With blocksize=256__
Run   1: 0.087097 s
  Run   2: 0.085462 s
  Run   3: 0.075220 s
  Run   4: 0.071476 s
  Run   5: 0.072351 s

========================================
  Monte Carlo timing summary (1000 runs)
========================================
  Mean     : 0.073701 s
  Std dev  : 0.001131 s
  Median   : 0.073799 s
  Min      : 0.071091 s
  Max      : 0.087097 s
  95% CI   : [ 0.073631 , 0.073772 ] s
  CV       : 1.53 %
========================================

All runs produced consistent results.

Result (from warm-up run): 507805 12177.071289 400548 23157.615234 511786 34230.769531 511786 44824.339844

__With blocksize=512__
Run   1: 0.080173 s
  Run   2: 0.079012 s
  Run   3: 0.076031 s
  Run   4: 0.072437 s
  Run   5: 0.071471 s

========================================
  Monte Carlo timing summary (1000 runs)
========================================
  Mean     : 0.073533 s
  Std dev  : 0.001036 s
  Median   : 0.073568 s
  Min      : 0.071435 s
  Max      : 0.080173 s
  95% CI   : [ 0.073469 , 0.073598 ] s
  CV       : 1.41 %
========================================

All runs produced consistent results.

Result (from warm-up run): 507805 12177.071289 400548 23157.615234 511786 34230.769531 511786 44824.339844

__With blocksize=1024__
Run   1: 0.082403 s
  Run   2: 0.072486 s
  Run   3: 0.072119 s
  Run   4: 0.072540 s
  Run   5: 0.072144 s

========================================
  Monte Carlo timing summary (1000 runs)
========================================
  Mean     : 0.074361 s
  Std dev  : 0.000977 s
  Median   : 0.074522 s
  Min      : 0.072021 s
  Max      : 0.082403 s
  95% CI   : [ 0.074301 , 0.074422 ] s
  CV       : 1.31 %
========================================

All runs produced consistent results.

Result (from warm-up run): 507805 12177.071289 400548 23157.615234 511786 34230.769531 511786 44824.339844

___

Using test_files02* (made for general workload)

__With blocksize=32__
Run   1: 0.023602 s
  Run   2: 0.023559 s
  Run   3: 0.023552 s
  Run   4: 0.023119 s
  Run   5: 0.022813 s

========================================
  Monte Carlo timing summary (1000 runs)
========================================
  Mean     : 0.018112 s
  Std dev  : 0.000441 s
  Median   : 0.018075 s
  Min      : 0.018009 s
  Max      : 0.023602 s
  95% CI   : [ 0.018085 , 0.018139 ] s
  CV       : 2.44 %
========================================

All runs produced consistent results.

Result (from warm-up run): 17197 1654.755371 17223 3274.642578 17229 5727.363281 17222 8155.511230 15849 11403.597656 15924 14647.188477

__With blocksize=64__
Run   1: 0.023177 s
  Run   2: 0.023632 s
  Run   3: 0.023625 s
  Run   4: 0.023650 s
  Run   5: 0.023622 s

========================================
  Monte Carlo timing summary (1000 runs)
========================================
  Mean     : 0.018171 s
  Std dev  : 0.000492 s
  Median   : 0.018121 s
  Min      : 0.017965 s
  Max      : 0.023650 s
  95% CI   : [ 0.018140 , 0.018201 ] s
  CV       : 2.71 %
========================================

All runs produced consistent results.

Result (from warm-up run): 17197 1654.755371 17223 3274.642578 17229 5727.363281 17222 8155.511230 15849 11403.597656 15924 14647.188477

__With blocksize=128__
Run   1: 0.024897 s
  Run   2: 0.024172 s
  Run   3: 0.024080 s
  Run   4: 0.024045 s
  Run   5: 0.024081 s

========================================
  Monte Carlo timing summary (1000 runs)
========================================
  Mean     : 0.019074 s
  Std dev  : 0.000375 s
  Median   : 0.019048 s
  Min      : 0.018987 s
  Max      : 0.024897 s
  95% CI   : [ 0.019051 , 0.019097 ] s
  CV       : 1.97 %
========================================

All runs produced consistent results.

Result (from warm-up run): 17197 1654.755371 17223 3274.642578 17229 5727.363281 17222 8155.511230 15849 11403.597656 15924 14647.188477

__With blocksize=256__
Run   1: 0.026459 s
  Run   2: 0.026440 s
  Run   3: 0.026435 s
  Run   4: 0.025686 s
  Run   5: 0.025552 s

========================================
  Monte Carlo timing summary (1000 runs)
========================================
  Mean     : 0.020259 s
  Std dev  : 0.000483 s
  Median   : 0.020221 s
  Min      : 0.020160 s
  Max      : 0.026459 s
  95% CI   : [ 0.020229 , 0.020289 ] s
  CV       : 2.38 %
========================================

All runs produced consistent results.

Result (from warm-up run): 17197 1654.755371 17223 3274.642578 17229 5727.363281 17222 8155.511230 15849 11403.597656 15924 14647.188477

__With blocksize=512__
Run   1: 0.026745 s
  Run   2: 0.026249 s
  Run   3: 0.025830 s
  Run   4: 0.025853 s
  Run   5: 0.025863 s

========================================
  Monte Carlo timing summary (1000 runs)
========================================
  Mean     : 0.020464 s
  Std dev  : 0.000407 s
  Median   : 0.020423 s
  Min      : 0.020394 s
  Max      : 0.026745 s
  95% CI   : [ 0.020438 , 0.020489 ] s
  CV       : 1.99 %
========================================

All runs produced consistent results.

Result (from warm-up run): 17197 1654.755371 17223 3274.642578 17229 5727.363281 17222 8155.511230 15849 11403.597656 15924 14647.188477

__With blocksize=1024__
Run   1: 0.041310 s
  Run   2: 0.040550 s
  Run   3: 0.039403 s
  Run   4: 0.039399 s
  Run   5: 0.032378 s

========================================
  Monte Carlo timing summary (1000 runs)
========================================
  Mean     : 0.031110 s
  Std dev  : 0.000583 s
  Median   : 0.031061 s
  Min      : 0.030985 s
  Max      : 0.041310 s
  95% CI   : [ 0.031074 , 0.031147 ] s
  CV       : 1.87 %
========================================

All runs produced consistent results.

Result (from warm-up run): 17197 1654.755371 17223 3274.642578 17229 5727.363281 17222 8155.511230 15849 11403.597656 15924 14647.188477










___
## Changelog of optimizations

Baseline parallel cuda program:
- Basic parallel implementation.
- 256 threads per block.
- `gridDim((layer_size + blockDim.x - 1) / blockDim.x, 1, 1)`

V2:
- Introduced removal of conditional code in kernel __update__.

V3:
- Introduced removal of conditional code in kernel __relax__.
- Optimized write instructions in kernel __bomb__. (buggy)

V4:
- Reverted write optimizations in kernel __bomb__ due to incorrect output.

V5:
- Remove layer_copy in global memory in favor of shared memory shared_layer.

## How to cluster

salloc -n 1 —gpus-per-task=1

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

salloc --gpus=1 --nodes=1 --gpus-per-task=1 --cpus-per-task=1 --time=00:15:00 --qos=students_limit

srun -N 1 -n 1 ./energy_storms_cuda 20000 test_files/test_02_a30k_p20k_w1 test_files/test_02_a30k_p20k_w2 test_files/test_02_a30k_p20k_w3 test_files/test_02_a30k_p20k_w4 test_files/test_02_a30k_p20k_w5 test_files/test_02_a30k_p20k_w6

## Profiling methodology

Profiling methodology:
- Running 10 times each variant of baseline parallel cuda program.
- Taking the median time of the 10 result.
- All variants use 256 threads per block.

## Results

### Sequential

Result: 17197 1654.755371 17223 3274.642578 17229 5727.363281 17222 8155.511230 15849 11403.597656 15924 14647.188477

1) Time: 14.669397
2) Time: 14.638959
3) Time: 14.769248
4) Time: 14.597273
5) Time: 14.617630
6) Time: 14.615136
7) Time: 14.621756
8) Time: 14.603289
9) Time: 14.608481
10) Time: 14.594200

### Baseline

Result: 17197 1654.755371 17223 3274.642578 17229 5727.363281 17222 8155.511230 15849 11403.597656 15924 14647.188477

1) Time: 0.026276
2) Time: 0.024507
3) Time: 0.024457
4) Time: 0.024224
5) Time: 0.024279
6) Time: 0.024414
7) Time: 0.024857
8) Time: 0.024304
9) Time: 0.024323
10) Time: 0.024284

### V2

Result: 17197 1654.755371 17223 3274.642578 17229 5727.363281 17222 8155.511230 15849 11403.597656 15924 14647.188477

1) Time: 0.025064
2) Time: 0.023531
3) Time: 0.023743
4) Time: 0.023770
5) Time: 0.023669
6) Time: 0.023481
7) Time: 0.023641
8) Time: 0.023621
9) Time: 0.023823
10) Time: 0.023747

### V3

Result: 17197 1654.755371 17223 3274.631104 17229 5727.361816 17222 8155.466309 15849 11403.617188 15924 14647.062500

1) Time: 0.029269
2) Time: 0.023397
3) Time: 0.023294
4) Time: 0.023407
5) Time: 0.023366
6) Time: 0.023193
7) Time: 0.023018
8) Time: 0.023168
9) Time: 0.023349
10) Time: 0.023615

### V4

Result: 17197 1654.755371 17223 3274.642578 17229 5727.363281 17222 8155.511230 15849 11403.597656 15924 14647.188477

1) Time: 0.022718
2) Time: 0.023617
3) Time: 0.023836
4) Time: 0.023518
5) Time: 0.024010
6) Time: 0.023678
7) Time: 0.023693
8) Time: 0.024341
9) Time: 0.023541
10) Time: 0.023788

### V5

Result: 17197 1654.755371 17223 3274.642578 17229 5727.363281 17222 8155.511230 15849 11403.597656 15924 14647.188477


1) 


___

nvcc -arch=sm_75 -c energy_storms_cuda_core.cu -lm -o energy_storms_cuda_core.o

nvcc -arch=sm_75 energy_storms_cuda.cpp energy_storms_cuda_core.o -lm -o energy_storms_cuda

./energy_storms_cuda 20000 test_files/test_02_a30k_p20k_w1 test_files/test_02_a30k_p20k_w2 test_files/test_02_a30k_p20k_w3 test_files/test_02_a30k_p20k_w4 test_files/test_02_a30k_p20k_w5 test_files/test_02_a30k_p20k_w6

____

Provare ad usare la memoria per le variabili costanti invece della cache L2 per il vettore delle palle

Usare meno registri nelle funzioni kernel

caching -> fare modo che l'array dei valori da leggere sia contiguo, cambiando l'ordine dei valori

can use compiler directives (like `__attribute__((aligned(64)))`) to explicitly align variables to cache line boundaries

prima di scrivere il risultato ottenuto, meglio fare un \_\_syncthreads o avere una copia del vettore sulla quale si opera.

Controllare ed richiedere che i threads siano allineati e le richieste al vettore dei valori sia allineato quando si richiede la lettura dei dati dal vettore (Coalescing)

Disabilitare L1 ?? -Xptxas -dlcm=cg __no__











___
Base + 64

Run   1: 0.025478 s
  Run   2: 0.025426 s
  Run   3: 0.024997 s
  Run   4: 0.024579 s
  Run   5: 0.024568 s
  Run   6: 0.024584 s
  Run   7: 0.022222 s
  Run   8: 0.019789 s
  Run   9: 0.019797 s
  Run  10: 0.019804 s
  Run  11: 0.019795 s
  Run  12: 0.019683 s
  Run  13: 0.019512 s
  Run  14: 0.019433 s
  Run  15: 0.019448 s
  Run  16: 0.019443 s
  Run  17: 0.019437 s
  Run  18: 0.019461 s
  Run  19: 0.019449 s
  Run  20: 0.019462 s
  Run  21: 0.019446 s
  Run  22: 0.019440 s


___
Claude a 256

Run   1: 0.023514 s
  Run   2: 0.022808 s
  Run   3: 0.022796 s
  Run   4: 0.022819 s
  Run   5: 0.022796 s
  Run   6: 0.018965 s
  Run   7: 0.018370 s
  Run   8: 0.018372 s
  Run   9: 0.018367 s
  Run  10: 0.018358 s
  Run  11: 0.018263 s
  Run  12: 0.018017 s
  Run  13: 0.018024 s
  Run  14: 0.018008 s
  Run  15: 0.018006 s
  Run  16: 0.018031 s
  Run  17: 0.018015 s
  Run  18: 0.018030 s
  Run  19: 0.018019 s
  Run  20: 0.018012 s

___

Claude refactor + 64

0.22



___


In CUDA, `__restrict__` is a keyword used with pointer arguments in a [kernel](https://docs.nvidia.com/cuda/cuda-c-programming-guide/) to tell the compiler that a specific pointer is the **only way** to access the data it points to. 

Why Use It?

The primary goal is to eliminate **pointer aliasing**, where two different pointers might refer to the same memory location. Without `__restrict__`, the compiler must be conservative; it assumes that writing to one pointer might change the data being read from another. 

By using `__restrict__`, you provide a "promise" that no aliasing occurs, which allows the compiler to: 

- **Reduce Redundant Loads**: If the compiler knows data won't change through another pointer, it can cache values in registers instead of re-reading them from global memory.
- **Reorder Instructions**: It can more aggressively rearrange code for better performance.
- **Enable Read-Only Cache**: When combined with the `const` keyword on devices with compute capability 3.5 or higher, it acts as a hint to use the GPU's dedicated **read-only data cache** (Texture Cache). 

Code Example

In the following kernel, `__restrict__` tells the compiler that `a`, `b`, and `c` do not overlap: 

cpp

```
__global__ void addKernel(const float* __restrict__ a, 
                          const float* __restrict__ b, 
                          float* __restrict__ c) {
    int i = threadIdx.x;
    c[i] = a[i] + b[i];
}
```

Use code with caution.

Critical Rules

- **The Contract**: If you use `__restrict__` and then actually _do_ alias the pointers (e.g., passing the same array for both `a` and `c`), you will trigger **undefined behavior** and likely get incorrect results.
- **Placement**: It is typically applied to raw pointer arguments in kernel or device function declarations.
- **All-or-Nothing**: For the optimizer to fully benefit, you should generally mark **all** related pointer arguments in the function as restricted.

