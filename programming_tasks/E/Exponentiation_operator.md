[1]: https://rosettacode.org/wiki/Exponentiation_operator

# [Exponentiation operator][1]

Function definition:

```ruby
func expon(_, { .is_zero }) { 1 }

func expon(base, exp { .is_neg }) {
    expon(1/base, -exp)
}

func expon(base, exp { .is_int }) {

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
0.00601051840721262208865514650638617581
```
