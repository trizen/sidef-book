[1]: http://rosettacode.org/wiki/Faulhaber's_formula

# [Faulhaber's formula][1]

```ruby
const AnyNum = require('Math::AnyNum')
const Poly   = require('Math::Polynomial')

Poly.string_config(Hash(
    fold_sign => true, prefix => "",
    suffix => "", variable => "n"
))

func anynum(n) {
    AnyNum.new(n.as_rat)
}

func faulhaber_formula(p) {
    (p+1).of { |j|
        Poly.monomial(p - j + 1)\
            .mul_const(anynum(bernoulli(j)))\
            .mul_const(anynum(binomial(p+1, j)))
    }.reduce(:add).div_const(p+1)
}

for p in (^10) {
    printf("%2d: %s\n", p, faulhaber_formula(p))
}
```

#### Output:
```
 0: n
 1: 1/2 n^2 + 1/2 n
 2: 1/3 n^3 + 1/2 n^2 + 1/6 n
 3: 1/4 n^4 + 1/2 n^3 + 1/4 n^2
 4: 1/5 n^5 + 1/2 n^4 + 1/3 n^3 - 1/30 n
 5: 1/6 n^6 + 1/2 n^5 + 5/12 n^4 - 1/12 n^2
 6: 1/7 n^7 + 1/2 n^6 + 1/2 n^5 - 1/6 n^3 + 1/42 n
 7: 1/8 n^8 + 1/2 n^7 + 7/12 n^6 - 7/24 n^4 + 1/12 n^2
 8: 1/9 n^9 + 1/2 n^8 + 2/3 n^7 - 7/15 n^5 + 2/9 n^3 - 1/30 n
 9: 1/10 n^10 + 1/2 n^9 + 3/4 n^8 - 7/10 n^6 + 1/2 n^4 - 3/20 n^2
```
