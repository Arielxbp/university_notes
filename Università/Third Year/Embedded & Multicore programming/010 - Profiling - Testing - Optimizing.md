
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