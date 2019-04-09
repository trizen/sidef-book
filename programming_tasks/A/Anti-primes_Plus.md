[1]: https://rosettacode.org/wiki/Anti-primes_Plus

# [Anti-primes Plus][1]

a(n) is the smallest number with exactly n divisors ([A005179](https://oeis.org/A005179)).

```ruby
func n_divisors(n) {
    1..Inf -> first_by { .sigma0 == n }
}
 
say 15.of { n_divisors(_+1) }
```

#### Output:
```
[1, 2, 4, 6, 16, 12, 64, 24, 36, 48, 1024, 60, 4096, 192, 144]
```


a(n) is the smallest number &gt; a(n-1) with exactly n divisors ([A069654](https://oeis.org/A069654)).

```ruby
func n_divisors(n, from=1) {
    from..Inf -> first_by { .sigma0 == n }
}
 
with (1) { |from|
    say 15.of { from = n_divisors(_+1, from) }
}
```

#### Output:
```
[1, 2, 4, 6, 16, 18, 64, 66, 100, 112, 1024, 1035, 4096, 4288, 4624]
```
