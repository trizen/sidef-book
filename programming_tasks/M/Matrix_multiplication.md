[1]: http://rosettacode.org/wiki/Matrix_multiplication

# [Matrix multiplication][1]

```ruby
func matrix_multi(a, b) {
    var m = [[]]
    for r in ^a {
        for c in ^b[0] {
            for i in ^b {
                m[r][c] := 0 += (a[r][i] * b[i][c])
            }
        }
    }
    return m
}
 
var a = [
          [1, 2],
          [3, 4],
          [5, 6],
          [7, 8]
        ]
 
var b = [
          [1, 2, 3],
          [4, 5, 6]
        ]
 
for line in matrix_multi(a, b) {
    say line.map{|i|'%3d' % i }.join(', ')
}
```

#### Output:
```
  9,  12,  15
 19,  26,  33
 29,  40,  51
 39,  54,  69
```
