[1]: https://rosettacode.org/wiki/Cholesky_decomposition

# [Cholesky decomposition][1]

```ruby
func cholesky(matrix) {
    var chol = matrix.len.of { matrix.len.of(0) }
    for row in ^matrix {
        for col in (0..row) {
            var x = matrix[row][col]
            for i in (0..col) {
                x -= (chol[row][i] * chol[col][i])
            }
            chol[row][col] = (row == col ? x.sqrt : x/chol[col][col])
        }
    }
    return chol
}
```


Examples:

```ruby
var example1 = [ [ 25, 15, -5 ],
                 [ 15, 18,  0 ],
                 [ -5,  0, 11 ] ]

say "Example 1:"
cholesky(example1).each { |row|
    say row.map {'%7.4f' % _}.join(' ')
}

var example2 = [ [ 18, 22,  54,  42],
                 [ 22, 70,  86,  62],
                 [ 54, 86, 174, 134],
                 [ 42, 62, 134, 106] ]

say "\nExample 2:"
cholesky(example2).each { |row|
    say row.map {'%7.4f' % _}.join(' ')
}
```

#### Output:
```
Example 1:
 5.0000  0.0000  0.0000
 3.0000  3.0000  0.0000
-1.0000  1.0000  3.0000

Example 2:
 4.2426  0.0000  0.0000  0.0000
 5.1854  6.5659  0.0000  0.0000
12.7279  3.0460  1.6497  0.0000
 9.8995  1.6246  1.8497  1.3926
```
