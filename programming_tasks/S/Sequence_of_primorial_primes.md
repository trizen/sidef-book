[1]: https://rosettacode.org/wiki/Sequence_of_primorial_primes

# [Sequence of primorial primes][1]

```ruby
func primorial_primes(n) {
 
    var k = 1
    var p = 2
    var P = 2
 
    var seq = []
    for (var i = 0; i < n; ++k) {
 
        if (is_prime(P-1) || is_prime(P+1)) {
            seq << k
            ++i
        }
 
        p.next_prime!
        P *= p
    }
 
    return seq
}
 
say primorial_primes(20)
```

#### Output:
```
[1, 2, 3, 4, 5, 6, 11, 13, 24, 66, 68, 75, 167, 171, 172, 287, 310, 352, 384, 457]
```