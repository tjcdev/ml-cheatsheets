# Python

### Parallel

TODO: Look up some of the materials on parallel processing in Python


### Vectorisation

Python for loops are inherently slower than their C counterpart.

This is why numpy offers vectorized actions on numpy arrays. It pushes the for loop you would usually do in Python down to the C level, which is much faster. numpy offers vectorized ("C level for loop") alternatives to things that otherwise would need to be done in an element-wise manner ("Python level for loop).

Methods that use Vectorisation:
- outer(a, b): Compute the outer product of two vectors.
- multiply(a, b): Matrix product of two arrays.
- dot(a, b): Dot product of two arrays.
- zeros((n, m)): Return a matrix of given shape and type, filled with zeros.