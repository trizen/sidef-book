[1]: https://rosettacode.org/wiki/Wilson_primes_of_order_n

# [Wilson primes of order n][1]

```ruby
func is_wilson_prime(p, n = 1) {
    var m = p*p
    (factorialmod(n-1, m) * factorialmod(p-n, m) - (-1)**n) % m == 0
}
 
var primes = 1.1e4.primes
 
say "  n: Wilson primes\n────────────────────"
 
for n in (1..11) {
    printf("%3d: %s\n", n, primes.grep {|p| is_wilson_prime(p, n) })
}
```

#### Output:
```
  n: Wilson primes
────────────────────
  1: [5, 13, 563]
  2: [2, 3, 11, 107, 4931]
  3: [7]
  4: [10429]
  5: [5, 7, 47]
  6: [11]
  7: [17]
  8: []
  9: [541]
 10: [11, 1109]
 11: [17, 2713]
```
