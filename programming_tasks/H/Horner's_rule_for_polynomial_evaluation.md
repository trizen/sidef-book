[1]: http://rosettacode.org/wiki/Horner's_rule_for_polynomial_evaluation

# [Horner's rule for polynomial evaluation][1]

Functional:

```ruby
func horner(coeff, x) {
    coeff.reverse.reduce { |a,b| a*x + b };
}
 
say horner([-19, 7, -4, 6], 3);   # => 128
```


Recursive:

```ruby
func horner(coeff, x) {
    coeff.len > 0
        && (coeff[0] + x*horner(coeff.ft(1), x));
}
 
say horner([-19, 7, -4, 6], 3);   # => 128
```