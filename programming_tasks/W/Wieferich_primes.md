[1]: https://rosettacode.org/wiki/Wieferich_primes

# [Wieferich primes][1]

```ruby
func is_wieferich_prime(p, base=2) {
    powmod(base, p-1, p**2) == 1
}
 
say ("Wieferich primes less than 5000: ", 5000.primes.grep(is_wieferich_prime))
```

#### Output:
```
Wieferich primes less than 5000: [1093, 3511]
```
