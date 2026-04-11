# Speedup sequential versus parallel (seed 42, 64 threads)

Particles have fixed max possible energy and position
The number of particles varies: 1k, 10k, 100k, ...

test_file_p1k

SEQ:
Time: 5.561163
Result: 85349 2373.485596

CUDA:
Time: 0.006066
Result: 85349 2373.485596

test_file_p10k

SEQ:
Time: 55.507657
Result: 354996 16135.265625

CUDA:
Time: 0.046404
Result: 354996 16135.265625

test_file_p100k

SEQ:
Time: 554.678401
Result: 497976 144214.265625

CUDA:
Time: 0.355378
Result: 497976 144214.265625




# Execution versus dataset size (seed 42, 64 threads, fixed max energy and positions, variable number of particles)

test_file_1m

Time: 3.590673
Time: 3.577035
Time: 3.590051
Time: 3.592985
Time: 3.590416
Result: 497226 1422306.500000

___

test_file_500k

Time: 1.829695
Time: 1.783926
Time: 1.782347
Time: 1.783749
Time: 1.781533
Result: 518766 713671.000000

___

test_file_100k

Time: 0.358331
Time: 0.355458
Time: 0.355442
Time: 0.355852
Time: 0.355713
Result: 497976 144214.265625

___

test_file_10k

Time: 0.045869
Time: 0.046849
Time: 0.045984
Time: 0.046870
Time: 0.045852
Result: 354996 16135.265625

___

test_file_1k

Time: 0.006038
Time: 0.006144
Time: 0.006054
Time: 0.006137
Time: 0.006126
Result: 85349 2373.485596