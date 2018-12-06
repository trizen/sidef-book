[1]: https://rosettacode.org/wiki/Totient_function

# [Totient function][1]

The Euler totient function is built-in as **Number.euler\_phi()**, but we can easily re-implement it using its multiplicative property: **phi(p^k) = (p-1)\*p^(k-1)**.

```ruby
func 𝜑(n) {
    n.factor_exp.prod {|p|
        (p[0]-1) * p[0]**(p[1]-1)
    }
}
```
```ruby
for n in (1..25) {
    var totient = 𝜑(n)
    printf("𝜑(%2s) = %3s%s\n", n, totient, totient==(n-1) ? ' - prime' : '')
}
```
```ruby
[100, 1_000, 10_000, 100_000].each {|limit|
    var pi = (1..limit -> count_by {|n| 𝜑(n) == (n-1) })
    say "Number of primes <= #{limit}: #{pi}"
}
```

#### Output:
```
Number of primes <= 100: 25
Number of primes <= 1000: 168
Number of primes <= 10000: 1229
Number of primes <= 100000: 9592
```