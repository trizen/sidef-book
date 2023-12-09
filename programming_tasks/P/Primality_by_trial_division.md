[1]: https://rosettacode.org/wiki/Primality_by_trial_division

# [Primality by trial division][1]

```ruby
func is_prime(a) {
  given (a) {
    when (2)                   { true  }
    case (a <= 1 || a.is_even) { false }
    default                    { 3 .. a.isqrt -> any { .divides(a) } -> not }
  }
}
```


Alternative version, excluding multiples of 2 and 3:

```ruby
func is_prime(n) {
    return (n >= 2) if (n < 4)
    return false if (n%%2 || n%%3)
    for k in (5 .. n.isqrt -> by(6)) {
        return false if (n%%k || n%%(k+2))
    }
    return true
}
```
