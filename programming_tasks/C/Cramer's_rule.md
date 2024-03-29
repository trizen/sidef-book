[1]: https://rosettacode.org/wiki/Cramer's_rule

# [Cramer's rule][1]

```ruby
func cramers_rule(A, terms) {
    gather {
        for i in ^A {
            var Ai = A.map{.map{_}}
            for j in ^terms {
                Ai[j][i] = terms[j]
            }
            take(Ai.det)
        }
    } »/» A.det
}

var matrix = [
    [2, -1,  5,  1],
    [3,  2,  2, -6],
    [1,  3,  3, -1],
    [5, -2, -3,  3],
]

var free_terms = [-3, -32, -47, 49]
var (w, x, y, z) = cramers_rule(matrix, free_terms)...

say "w = #{w}"
say "x = #{x}"
say "y = #{y}"
say "z = #{z}"
```

#### Output:
```
w = 2
x = -12
y = -4
z = 1
```
