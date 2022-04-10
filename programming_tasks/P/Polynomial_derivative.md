[1]: https://rosettacode.org/wiki/Polynomial_derivative

# [Polynomial derivative][1]

```ruby
func derivative(f) {
    Poly(f.coeffs.map_2d{|e,k| [e-1, k*e] }.flat...)
}
 
var coeffs = [
    [5],
    [4,-3],
    [-1,6,5],
    [-4,3,-2,1],
    [-1, 6, 5],
    [1,1,0,-1,-1],
]
 
for c in (coeffs) {
    var poly = Poly(c.flip)
    var derv = derivative(poly)
 
    var d = { derv.coeff(_) }.map(0..derv.degree)
 
    say "Polynomial : #{'%20s' % c} = #{poly}"
    say "Derivative : #{'%20s' % d} = #{derv || 0}\n"
}
```

#### Output:
```
Polynomial :                  [5] = 5
Derivative :                  [0] = 0

Polynomial :              [4, -3] = -3*x + 4
Derivative :                 [-3] = -3

Polynomial :           [-1, 6, 5] = 5*x^2 + 6*x - 1
Derivative :              [6, 10] = 10*x + 6

Polynomial :       [-4, 3, -2, 1] = x^3 - 2*x^2 + 3*x - 4
Derivative :           [3, -4, 3] = 3*x^2 - 4*x + 3

Polynomial :           [-1, 6, 5] = 5*x^2 + 6*x - 1
Derivative :              [6, 10] = 10*x + 6

Polynomial :    [1, 1, 0, -1, -1] = -x^4 - x^3 + x + 1
Derivative :       [1, 0, -3, -4] = -4*x^3 - 3*x^2 + 1
```
