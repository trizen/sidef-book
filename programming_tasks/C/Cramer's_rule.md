[1]: http://rosettacode.org/wiki/Cramer's_rule

# [Cramer's rule][1]

```ruby
func det(a) {
    a = a.map{.map{_}}
    var sign = +1
    var pivot = 1

    for k in ^a {
      var r = (k+1 .. a.end)
      var previous_pivot = pivot

      if ((pivot = a[k][k])==0) {
        a.swap(r.first_by { |i|
            a[i][k] != 0
        } \\ (return 0), k)
        pivot = a[k][k]
        sign = -sign
      }

      for i,j in (r ~X r) {
        ((a[i][j] *= pivot)
            -= a[i][k]*a[k][j]
        ) /= previous_pivot
      }
    }
    sign * pivot
}

func cramers_rule(A, terms) {
    gather {
        for i in ^A {
            var Ai = A.map{.map{_}}
            for j in ^terms {
                Ai[j][i] = terms[j]
            }
            take(det(Ai))
        }
    } »/» det(A)
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
