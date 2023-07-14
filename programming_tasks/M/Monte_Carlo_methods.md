[1]: https://rosettacode.org/wiki/Monte_Carlo_methods

# [Monte Carlo methods][1]

```ruby
func monteCarloPi(nthrows) {
    4 * (^nthrows -> count_by {
        hypot(1.rand(2) - 1, 1.rand(2) - 1) < 1
    }) / nthrows
}
 
for n in [1e2, 1e3, 1e4, 1e5, 1e6] {
    printf("%9d: %07f\n", n, monteCarloPi(n))
}
```

#### Output:
```
      100: 3.320000
     1000: 3.120000
    10000: 3.169600
   100000: 3.138920
  1000000: 3.142344
```