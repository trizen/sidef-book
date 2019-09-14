[1]: https://rosettacode.org/wiki/Semiprime

# [Semiprime][1]

Built-in:

```ruby
say is_semiprime(2**128 + 1)   #=> true
say is_semiprime(2**256 - 1)   #=> false
```

User-defined function, with trial division up to a given bound `B`:

```ruby
func is_semiprime(n, B=1e4) {

    with (n.trial_factor(B)) { |f|
        return false if (f.len > 2)
        return f.all { .is_prime } if (f.len == 2)
    }

    n.factor.len == 2
}

say [2,4,99,100,1679,32768,1234567,9876543,900660121].grep(is_semiprime)
```

#### Output:
```
[4, 1679, 1234567, 900660121]
```
