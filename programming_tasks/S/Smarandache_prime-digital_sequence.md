[1]: https://rosettacode.org/wiki/Smarandache_prime-digital_sequence

# [Smarandache prime-digital sequence][1]

```ruby
func is_prime_digital(n) {
    n.is_prime && n.digits.all { .is_prime }
}
 
say is_prime_digital.first(25).join(',')
say is_prime_digital.nth(100)
```

#### Output:
```
2,3,5,7,23,37,53,73,223,227,233,257,277,337,353,373,523,557,577,727,733,757,773,2237,2273
33223
```
