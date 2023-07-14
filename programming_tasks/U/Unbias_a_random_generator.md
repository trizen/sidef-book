[1]: https://rosettacode.org/wiki/Unbias_a_random_generator

# [Unbias a random generator][1]

```ruby
func randN (n) {
    n.rand / (n-1) -> int
}
 
func unbiased(n) {
    var n1 = nil
    do { n1 = randN(n) } while (n1 == randN(n))
    return n1
}
 
var iterations = 1000
 
for n in (3..6) {
    var raw = []
    var fixed = []
    iterations.times {
          raw[    randN(n) ] := 0 ++
        fixed[ unbiased(n) ] := 0 ++
    }
    printf("N=%d   randN: %s, %4.1f%%   unbiased: %s, %4.1f%%\n",
        n, [raw, fixed].map {|a| (a.dump, a[1] * 100 / iterations) }...)
}
```

#### Output:
```
N=3   randN: [661, 339], 33.9%   unbiased: [497, 503], 50.3%
N=4   randN: [765, 235], 23.5%   unbiased: [493, 507], 50.7%
N=5   randN: [812, 188], 18.8%   unbiased: [509, 491], 49.1%
N=6   randN: [820, 180], 18.0%   unbiased: [510, 490], 49.0%
```