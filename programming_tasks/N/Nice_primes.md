[1]: https://rosettacode.org/wiki/Nice_primes

# [Nice primes][1]

```ruby
func digital_root(n, base=10) {
    while (n.len(base) > 1) {
        n = n.sumdigits(base)
    }
    return n
}
 
say primes(500, 1000).grep { digital_root(_).is_prime }
```

#### Output:
```
[509, 547, 563, 569, 587, 599, 601, 617, 619, 641, 653, 659, 673, 677, 691, 709, 727, 743, 761, 797, 821, 839, 853, 857, 887, 907, 911, 929, 941, 947, 977, 983, 997]
```
