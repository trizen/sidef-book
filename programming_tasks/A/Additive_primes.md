[1]: https://rosettacode.org/wiki/Additive_primes

# [Additive primes][1]

```ruby
func additive_primes(upto, base = 10) {
    upto.primes.grep { .sumdigits(base).is_prime }
}
 
additive_primes(500).each_slice(10, {|*a|
    a.map { '%3s' % _ }.join(' ').say
})
```

#### Output:
```
  2   3   5   7  11  23  29  41  43  47
 61  67  83  89 101 113 131 137 139 151
157 173 179 191 193 197 199 223 227 229
241 263 269 281 283 311 313 317 331 337
353 359 373 379 397 401 409 421 443 449
461 463 467 487
```
