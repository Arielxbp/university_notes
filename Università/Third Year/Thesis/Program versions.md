___

`qr_ttnn.py`: base implementation of qr decomposition, no optimizations like householder
`qr_householder_ttnn.py`: changed base implementation to householder implementation
`qr_householder__ttnn_v2.py`: changed masking strategy during mathematical column zeroing phase after computing it (making so 0.000xy becomes 0 for accuracy purposes)

`qr_householder_ttnn_v3.py`: changed `zero_out_above_index` to produce a smaller matrix mask from a full matrix to a single column


tall skinny qr

factor panel must remain in fp32

increase block size to 64

blocked approach to drop syncronization for every vector norm and host to device upload for every mask -> so batching updates

===

compute householder vectors in fp32 on host

bundle reflectors into a single compact block representation -> to then perform a single matmul

extract the strcitly upper-triangular matrix T on the host and scales its diagonal using the vector norms

WY blocked representation -> casting 98%~ of total FLOPs as compute-bound level3 matrix matrix multiplications

tsqr parallelization -> replaced sequential column loops for tall matrices


add additional timings for every function used in the main function, summing them to then display them in the end.
```python
start_time = get_time()
func()
end_time = get_time()
timings.get(this_func_time) + (end_time + start_time)
# do this for every function
```
