[1]: https://rosettacode.org/wiki/Faulhaber's_formula

# [Faulhaber's formula][1]

```ruby
func faulhaber_formula(p) {
    (p+1).of { |j|
        Poly(p - j + 1 => 1) * bernoulli(j) * binomial(p+1, j)
    }.sum / (p+1)
}

for p in (^10) {
    printf("%2d: %s\n", p, faulhaber_formula(p))
}
```

#### Output:
```
 0: x
 1: 1/2*x^2 + 1/2*x
 2: 1/3*x^3 + 1/2*x^2 + 1/6*x
 3: 1/4*x^4 + 1/2*x^3 + 1/4*x^2
 4: 1/5*x^5 + 1/2*x^4 + 1/3*x^3 - 1/30*x
 5: 1/6*x^6 + 1/2*x^5 + 5/12*x^4 - 1/12*x^2
 6: 1/7*x^7 + 1/2*x^6 + 1/2*x^5 - 1/6*x^3 + 1/42*x
 7: 1/8*x^8 + 1/2*x^7 + 7/12*x^6 - 7/24*x^4 + 1/12*x^2
 8: 1/9*x^9 + 1/2*x^8 + 2/3*x^7 - 7/15*x^5 + 2/9*x^3 - 1/30*x
 9: 1/10*x^10 + 1/2*x^9 + 3/4*x^8 - 7/10*x^6 + 1/2*x^4 - 3/20*x^2
```
