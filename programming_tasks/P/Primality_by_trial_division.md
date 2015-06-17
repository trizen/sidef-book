[1]: http://rosettacode.org/wiki/Primality_by_trial_division

# [Primality by trial division][1]

```ruby
func is_prime(a) {
  given (a)
    case (a == 2)              { true  }
    case (a <= 1 || a.is_even) { false }
    default                    { 3 .. a.sqrt any { a %% _ } not };
}
```