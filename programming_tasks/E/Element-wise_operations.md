[1]: https://rosettacode.org/wiki/Element-wise_operations

# [Element-wise operations][1]

The built-in metaoperators \`~W&lt;op&gt;\`, \`~S&lt;op&gt;\` and \`~RS&lt;op&gt;\` are defined for arbitrary nested arrays.

```ruby
var m1 = [[3,1,4],[1,5,9]]
var m2 = [[2,7,1],[8,2,2]]
 
say ":: Matrix-matrix operations"
say (m1 ~W+  m2)
say (m1 ~W-  m2)
say (m1 ~W*  m2)
say (m1 ~W/  m2)
say (m1 ~W// m2)
say (m1 ~W** m2)
say (m1 ~W%  m2)
 
say "\n:: Matrix-scalar operations"
say (m1 ~S+  42)
say (m1 ~S-  42)
say (m1 ~S/  42)
say (m1 ~S** 10)
# ...
 
say "\n:: Scalar-matrix operations"
say (m1 ~RS+  42)
say (m1 ~RS-  42)
say (m1 ~RS/  42)
say (m1 ~RS** 10)
# ...
```

#### Output:
```
:: Matrix-matrix operations
[[5, 8, 5], [9, 7, 11]]
[[1, -6, 3], [-7, 3, 7]]
[[6, 7, 4], [8, 10, 18]]
[[3/2, 1/7, 4], [1/8, 5/2, 9/2]]
[[1, 0, 4], [0, 2, 4]]
[[9, 1, 4], [1, 25, 81]]
[[1, 1, 0], [1, 1, 1]]

:: Matrix-scalar operations
[[45, 43, 46], [43, 47, 51]]
[[-39, -41, -38], [-41, -37, -33]]
[[1/14, 1/42, 2/21], [1/42, 5/42, 3/14]]
[[59049, 1, 1048576], [1, 9765625, 3486784401]]

:: Scalar-matrix operations
[[45, 43, 46], [43, 47, 51]]
[[39, 41, 38], [41, 37, 33]]
[[14, 42, 21/2], [42, 42/5, 14/3]]
[[1000, 10, 10000], [10, 100000, 1000000000]]
```