# Polynomial

The `Polynomial` class implements support for [polynomials](https://en.wikipedia.org/wiki/Polynomial).

```ruby
say Polynomial(5)                   # monomial: x^5
say Polynomial([1,2,3,4])           # x^3 + 2*x^2 + 3*x + 4
say Polynomial(5 => 3, 2 => 10)     # 3*x^5 + 10*x^2
```

Also aliased as `Poly()`:

```ruby
var a = Poly([1,2,3])
var b = Poly([4,5,-6,7])

say a+b     #=> 4*x^3 + 6*x^2 - 4*x + 10
say a-b     #=> -4*x^3 - 4*x^2 + 8*x - 4
say a*b     #=> 4*x^5 + 13*x^4 + 16*x^3 + 10*x^2 - 4*x + 21

say 42-a    #=> -x^2 - 2*x + 39
say 42+b    #=> 4*x^3 + 5*x^2 - 6*x + 49
say 42*b    #=> 168*x^3 + 210*x^2 - 252*x + 294

say a/42    #=> 1/42*x^2 + 1/21*x + 1/14
say b/42    #=> 2/21*x^3 + 5/42*x^2 - 1/7*x + 1/6
```
