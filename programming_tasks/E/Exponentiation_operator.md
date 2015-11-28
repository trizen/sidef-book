[1]: http://rosettacode.org/wiki/Exponentiation_operator

# [Exponentiation operator][1]

Function definition:

```ruby
func expon(base, exp) {
  exp.is_int  || die "Exponent '#{exp}' must be an integer!"
  exp.is_zero && return 1
  exp.is_neg  && ((base, exp) = (1/base, -exp))
 
  var c = 1
  while (exp > 1) {
    c *= base if exp.is_odd
    base *= base
    exp >>= 1
  }
 
  return (base * c)
}
 
say expon(3, 10)
say expon(5.5, -3)
```


Operator definition:

```ruby
class Number {
    method ⊙(exp) {
        expon(self, exp)
    }
}
 
say (3 ⊙ 10)
say (5.5 ⊙ -3)
```

#### Output:
```
59049
0.006010518407212622088655146506386175807661607813673929376408715251690458302028550142749812171299774605559729526671675432
```