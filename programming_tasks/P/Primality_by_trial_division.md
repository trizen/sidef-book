[1]: http://rosettacode.org/wiki/Primality_by_trial_division

# [Primality by trial division][1]

```ruby
func is_prime(a) {
  given (a) {
    when (2)                   { true  }
    when (a <= 1 || a.is_even) { false }
    default                    { 3 ... a.sqrt -> any { .divides(a) } -> not }
  }
}
```