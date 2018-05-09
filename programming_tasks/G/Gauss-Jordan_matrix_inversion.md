[1]: https://rosettacode.org/wiki/Gauss-Jordan_matrix_inversion

# [Gauss-Jordan matrix inversion][1]

```ruby
func rref (M) {
    var (j, rows, cols) = (0, M.len, M[0].len)
 
    for r in (^rows) {
        j < cols || return M
 
        var i = r
        while (!M[i][j]) {
            ++i == rows || next
            i = r
            ++j == cols && return M
        }
 
        M[i, r] = M[r, i] if (r != i)
        M[r] = (M[r] »/» M[r][j])
 
        for n in (^rows) {
            next if (n == r)
            M[n] = (M[n] »-« (M[r] »*» M[n][j]))
        }
        ++j
    }
 
    return M
}
 
func gauss_jordan_invert (M) {
 
    var I = M.len.of {|i|
        M.len.of {|j|
            i == j ? 1 : 0
        }
    }
 
    var A = gather {
        ^M -> each {|i| take(M[i] + I[i]) }
    }
 
    rref(A).map { .last(M.len) }
}
 
var A = [
    [-1, -2, 3, 2],
    [-4, -1, 6, 2],
    [ 7, -8, 9, 1],
    [ 1, -2, 1, 3],
]
 
say gauss_jordan_invert(A).map {
    .map { "%6s" % .as_rat }.join("  ")
}.join("\n")
```

#### Output:
```
-21/23   17/69  13/138   19/46
-38/23   15/23    1/23   15/23
-16/23   25/69  11/138    9/46
-13/23   16/69   -2/69   13/23
```