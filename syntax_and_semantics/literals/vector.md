# Vector

The `Vector` built-in class (which is a child of the `Array` class), provides support for defining and working with vectors:

```ruby
Vector(1, 2, 3, 4, 5)
```

## Operations

```ruby
var A = Vector(1, 2, 3, 4)
var B = Vector(9, 8, 7, 6)

say (A + B)                    # vector entrywise addition
say (A - B)                    # vector entrywise subtraction
say (A * B)                    # cross product

say (A + 42)                   # vector-scalar addition
say (A - 42)                   # vector-scalar subtraction
say (A * 42)                   # vector-scalar multiplication
say (A / 42)                   # vector-scalar division

say A.sum                      # vector sum
say A.prod                     # vector product

say A.norm                     # normalized value: sum of squares
say A.manhattan_norm           # Manhattan normalized: sum of absolute values

say A.dist(B)                  # distance between two vectors
say A.dist_norm(B)             # distance squared between two vectors
say A.manhattan_dist(B)        # Manhattan distance between two vectors
say A.chebyshev_dist(B)        # Chebyshev distance between two vectors
```
