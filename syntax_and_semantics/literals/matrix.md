# Matrix

The `Matrix` built-in class (which is a child of the `Array` class), provides support for defining and working with matrices:

```ruby
Matrix(
    [1, 2],
    [3, 4],
)
```

## Operations

A subset of `Matrix` operations are included in the following example:

```ruby
var A = Matrix(
    [2, -3,  1],
    [1, -2, -2],
    [3, -4,  1],
)

var B = Matrix(
    [9, -3, -2],
    [3, -1,  7],
    [2, -4, -8],
)

say (A + B)     # matrix addition
say (A - B)     # matrix subtraction
say (A * B)     # matrix multiplication
say (A / B)     # matrix division

say (A + 42)    # matrix-scalar addition
say (A - 42)    # matrix-scalar subtraction
say (A * 42)    # matrix-scalar multiplication
say (A / 42)    # matrix-scalar division

say A**20       # matrix exponentation
say A**-1       # matrix inverse: A^-1
say A**-2       # (A^2)^-1

say B.det             # matrix determinant
say B.solve([1,2,3])  # solve a system of linear equations
```
