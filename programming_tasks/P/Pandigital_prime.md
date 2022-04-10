[1]: https://rosettacode.org/wiki/Pandigital_prime

# [Pandigital prime][1]

```ruby
func largest_pandigital_prime(base = 10, a = 1, b = base-1) {
 
    for n in (b `downto` 1) {
 
        var digits = @(a..n -> flip)
 
        if (base == 10) {   # check for divisibility by 3
            digits.sum % 3 == 0 && next
        }
 
        digits.permutations { |*p|
            var v = p.flip.digits2num(base)
            return v if v.is_prime
        }
    }
 
    return nil
}
 
say ("Max pandigital prime over [1, 9] is: ", largest_pandigital_prime(a: 1))
say ("Max pandigital prime over [0, 9] is: ", largest_pandigital_prime(a: 0))
```

#### Output:
```
Max pandigital prime over [1, 9] is: 7652413
Max pandigital prime over [0, 9] is: 76540231
```
