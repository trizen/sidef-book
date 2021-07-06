[1]: https://rosettacode.org/wiki/Erdős-primes

# [Erdős-primes][1]

```ruby
func is_erdos_prime(p) {
 
    return true  if p==2
    return false if !p.is_prime
 
    var f = 1
 
    for (var k = 2; f < p; k++) {
        p - f -> is_composite || return false
        f *= k
    }
 
    return true
}
 
say ("Erdős primes <= 2500: ", 1..2500 -> grep(is_erdos_prime))
say ("The 7875th Erdős prime is: ", is_erdos_prime.nth(7875))
```

#### Output:
```
Erdős primes <= 2500: [2, 101, 211, 367, 409, 419, 461, 557, 673, 709, 769, 937, 967, 1009, 1201, 1259, 1709, 1831, 1889, 2141, 2221, 2309, 2351, 2411, 2437]
The 7875th Erdős prime is: 999721
```
