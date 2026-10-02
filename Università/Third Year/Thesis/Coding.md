___

```python
np.linalg.norm(matrix[:, i], 2)

# becomes

def norm(input_list):
	sum = 0
	for value in input_list:
	sum += value*value
	return math.sqrt(sum)
```

## qr_ttnn (base)
- Base QR decomposition algorithm

## V1
- Base QR householder

## V2
- Changed matrix mask creation function (zero_out_above_index) from ttnn native to Pytorch

## V3
- Improved matrix mask creation function (zero_out_above_index) to use vectors (single columns) instead of full $M\times N$ matrices.

## V4 (and benchmark_v4)
- Improved householder approach by holding its updates in blocks (blocked householder)
- Delegated non-math and data movement operations to Pytorch
- Improved accuracy by dropping bfloat16 in favor of float32 (not fully supported, WIP)

## V5 (and benchmark_v5)
- Deprecated
- Removed V5 since it did not improve upon V4
- Supposedly should have better benchmarks by separating $Q$ matrix updates from the main loop

## V6
- Added support for non-square matrices
- Fully transitioned to float32 dtype
- Added math accuracy debug tests.

## V7 (wip)
- Completed the separation of all linear algebra math operations to the device
