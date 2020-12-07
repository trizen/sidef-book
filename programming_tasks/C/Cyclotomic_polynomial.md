[1]: https://rosettacode.org/wiki/Cyclotomic_polynomial

# [Cyclotomic polynomial][1]

Solution based on polynomial interpolation (slow).

```ruby
var Poly = require('Math::Polynomial')
Poly.string_config(Hash(fold_sign => true, prefix => "", suffix => ""))
 
func poly_interpolation(v) {
    v.len.of {|n| v.len.of {|k| n**k } }.msolve(v)
}
 
say "First 30 cyclotomic polynomials:"
for k in (1..30) {
    var a = (k+1).of { cyclotomic(k, _) }
    var Φ = poly_interpolation(a)
    say ("Φ(#{k}) = ", Poly.new(Φ...))
}
 
say "\nSmallest cyclotomic polynomial with n or -n as a coefficient:"
for n in (1..10) {  # very slow
    var k = (1..Inf -> first {|k|
        poly_interpolation((k+1).of { cyclotomic(k, _) }).first { .abs == n }
    })
    say "Φ(#{k}) has coefficient with magnitude #{n}"
}
```


Slightly faster solution, using the **Math::Polynomial::Cyclotomic** Perl module.

```ruby
var Poly = require('Math::Polynomial')
           require('Math::Polynomial::Cyclotomic')
 
Poly.string_config(Hash(fold_sign => true, prefix => "", suffix => ""))
 
say "First 30 cyclotomic polynomials:"
for k in (1..30) {
    say ("Φ(#{k}) = ", Poly.new.cyclotomic(k))
}
 
say "\nSmallest cyclotomic polynomial with n or -n as a coefficient:"
for n in (1..10) {
    var p = Poly.new
    var k = (1..Inf -> first {|k|
        [p.cyclotomic(k).coeff].first { .abs == n }
    })
    say "Φ(#{k}) has coefficient with magnitude = #{n}"
}
```

#### Output:
```
First 30 cyclotomic polynomials:
Φ(1) = x - 1
Φ(2) = x + 1
Φ(3) = x^2 + x + 1
Φ(4) = x^2 + 1
Φ(5) = x^4 + x^3 + x^2 + x + 1
Φ(6) = x^2 - x + 1
Φ(7) = x^6 + x^5 + x^4 + x^3 + x^2 + x + 1
Φ(8) = x^4 + 1
Φ(9) = x^6 + x^3 + 1
Φ(10) = x^4 - x^3 + x^2 - x + 1
Φ(11) = x^10 + x^9 + x^8 + x^7 + x^6 + x^5 + x^4 + x^3 + x^2 + x + 1
Φ(12) = x^4 - x^2 + 1
Φ(13) = x^12 + x^11 + x^10 + x^9 + x^8 + x^7 + x^6 + x^5 + x^4 + x^3 + x^2 + x + 1
Φ(14) = x^6 - x^5 + x^4 - x^3 + x^2 - x + 1
Φ(15) = x^8 - x^7 + x^5 - x^4 + x^3 - x + 1
Φ(16) = x^8 + 1
Φ(17) = x^16 + x^15 + x^14 + x^13 + x^12 + x^11 + x^10 + x^9 + x^8 + x^7 + x^6 + x^5 + x^4 + x^3 + x^2 + x + 1
Φ(18) = x^6 - x^3 + 1
Φ(19) = x^18 + x^17 + x^16 + x^15 + x^14 + x^13 + x^12 + x^11 + x^10 + x^9 + x^8 + x^7 + x^6 + x^5 + x^4 + x^3 + x^2 + x + 1
Φ(20) = x^8 - x^6 + x^4 - x^2 + 1
Φ(21) = x^12 - x^11 + x^9 - x^8 + x^6 - x^4 + x^3 - x + 1
Φ(22) = x^10 - x^9 + x^8 - x^7 + x^6 - x^5 + x^4 - x^3 + x^2 - x + 1
Φ(23) = x^22 + x^21 + x^20 + x^19 + x^18 + x^17 + x^16 + x^15 + x^14 + x^13 + x^12 + x^11 + x^10 + x^9 + x^8 + x^7 + x^6 + x^5 + x^4 + x^3 + x^2 + x + 1
Φ(24) = x^8 - x^4 + 1
Φ(25) = x^20 + x^15 + x^10 + x^5 + 1
Φ(26) = x^12 - x^11 + x^10 - x^9 + x^8 - x^7 + x^6 - x^5 + x^4 - x^3 + x^2 - x + 1
Φ(27) = x^18 + x^9 + 1
Φ(28) = x^12 - x^10 + x^8 - x^6 + x^4 - x^2 + 1
Φ(29) = x^28 + x^27 + x^26 + x^25 + x^24 + x^23 + x^22 + x^21 + x^20 + x^19 + x^18 + x^17 + x^16 + x^15 + x^14 + x^13 + x^12 + x^11 + x^10 + x^9 + x^8 + x^7 + x^6 + x^5 + x^4 + x^3 + x^2 + x + 1
Φ(30) = x^8 + x^7 - x^5 - x^4 - x^3 + x + 1

Smallest cyclotomic polynomial with n or -n as a coefficient:
Φ(1) has coefficient with magnitude = 1
Φ(105) has coefficient with magnitude = 2
Φ(385) has coefficient with magnitude = 3
Φ(1365) has coefficient with magnitude = 4
Φ(1785) has coefficient with magnitude = 5
Φ(2805) has coefficient with magnitude = 6
Φ(3135) has coefficient with magnitude = 7
^C
```
