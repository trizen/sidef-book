[1]: https://rosettacode.org/wiki/Resistor_mesh

# [Resistor mesh][1]

```ruby
var (w, h) = (10, 10)

var v = h.of { w.of(0) } # voltage
var f = h.of { w.of(0) } # fixed condition
var d = h.of { w.of(0) } # diff
var n = []               # neighbors

for i in ^h {
    for j in (1 ..^ w  ) { n[i][j] := [] << [i, j-1] }
    for j in (0 ..^ w-1) { n[i][j] := [] << [i, j+1] }
}

for j in ^w {
    for i in (1 ..^ h  ) { n[i][j] := [] << [i-1, j] }
    for i in (0 ..^ h-1) { n[i][j] := [] << [i+1, j] }
}

func set_boundary {
    f[1][1] = 1; f[6][7] = -1;
    v[1][1] = 1; v[6][7] = -1;
}

func calc_diff {
    var total_diff = 0
    for i,j in (^h ~X ^w) {
        var w = n[i][j].map { |a| v.dig(a...) }.sum
        d[i][j] = (w = (v[i][j] - w/n[i][j].len))
        f[i][j] || (total_diff += w*w)
    }
    total_diff
}

func iter {
    var diff = 1
    while (diff > 1e-24) {
        set_boundary()
        diff = calc_diff()
        for i,j in (^h ~X ^w) {
            v[i][j] -= d[i][j]
        }
    }

    var current = 3.of(0)
    for i,j in (^h ~X ^w) {
        current[ f[i][j] ] += (d[i][j] * n[i][j].len)
    }
    (current[1] - current[-1]) / 2
}

say "R = #{2 / iter()}"
```

#### Output:
```
R = 1.60899124172988902191367295307304
```
