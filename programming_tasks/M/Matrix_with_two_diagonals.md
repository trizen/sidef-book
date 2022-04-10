[1]: https://rosettacode.org/wiki/Matrix_with_two_diagonals

# [Matrix with two diagonals][1]

```ruby
func dual_diagonal(n) {
    n.of {|k|
        var r = (k.of(0) + [1] + (n - k - 1).of(0))
        r ~Z| r.reverse
    }
}
 
dual_diagonal(5).each{.join(' ').say}; say ''
dual_diagonal(6).each{.join(' ').say}
```

#### Output:
```
1 0 0 0 1
0 1 0 1 0
0 0 1 0 0
0 1 0 1 0
1 0 0 0 1

1 0 0 0 0 1
0 1 0 0 1 0
0 0 1 1 0 0
0 0 1 1 0 0
0 1 0 0 1 0
1 0 0 0 0 1
```
