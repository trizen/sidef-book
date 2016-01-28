[1]: http://rosettacode.org/wiki/Cramer's_rule

# [Cramer's rule][1]

```ruby
func det(A) {
    var dt = 0
    var rows = A.len
    A.each_index { |i|
        var (p1=1, p2=1)
        A[i].each_index { |j|
            p1 *= A[(j+i)%rows][j]
            p2 *= A[(j+i)%rows][-j]
        }
        dt += p1-p2
    }
    dt
}
 
func cramers_rule(A, terms) {
    var dxyz = []
    A.each_index { |i|
        var Ai = A.map{.map{_}}
        terms.each_index { |j|
            Ai[j][i] = terms[j]
        }
        dxyz[i] = det(Ai)
    }
    dxyz »/» det(A)
}
 
var matrix = [
    [2, -3,  1],
    [1, -2, -2],
    [3, -4,  1],
]
 
var free_terms = [4, -6, 5]
var (x, y, z) = cramers_rule(matrix, free_terms)...;
 
say "x = #{x}"
say "y = #{y}"
say "z = #{z}"
```

#### Output:
```
x = 2
y = 1
z = 3
```