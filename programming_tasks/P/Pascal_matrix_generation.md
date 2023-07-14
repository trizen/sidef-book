[1]: https://rosettacode.org/wiki/Pascal_matrix_generation

# [Pascal matrix generation][1]

```ruby
func grow_matrix(matrix, callback) {
    var m = matrix
    var s = m.len
    m[s][0] = callback(0, m[s-1][0], 0)
    m[0][s] = callback(m[0][s-1], 0, 0)
    {|i| m[i+1][s] = callback(m[i+1][s-1], m[i][s], m[i][s-1])} * (s-1)
    {|i| m[s][i+1] = callback(m[s][i], m[s-1][i+1], m[s-1][i])} * (s)
    return m
}

func transpose(matrix) {
    matrix[0].range.map{|i| matrix.map{_[i]} }
}

func madd_n_nw(m) { grow_matrix(m, ->(_, n, nw) { n + nw }) }
func madd_w_nw(m) { grow_matrix(m, ->(w, _, nw) { w + nw }) }
func madd_w_n(m)  { grow_matrix(m, ->(w, n, _)  { w + n  }) }

var functions = [madd_n_nw, madd_w_nw, madd_w_n].map { |f|
    func(n) {
        var r = [[1]]
        { f(r) } * n
        transpose(r)
    }
}

functions.map { |f|
    f(4).map { .map{ '%2s' % _ }.join(' ') }.join("\n")
}.join("\n\n").say
```

#### Output:
```
 1  1  1  1  1
 0  1  2  3  4
 0  0  1  3  6
 0  0  0  1  4
 0  0  0  0  1

 1  0  0  0  0
 1  1  0  0  0
 1  2  1  0  0
 1  3  3  1  0
 1  4  6  4  1

 1  1  1  1  1
 1  2  3  4  5
 1  3  6 10 15
 1  4 10 20 35
 1  5 15 35 70
```
