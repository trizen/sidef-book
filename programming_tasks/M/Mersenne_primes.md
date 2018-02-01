[1]: https://rosettacode.org/wiki/Mersenne_primes

# [Mersenne primes][1]

Uses the *is\_mersenne\_prime()* function from [Math::Prime::Util::GMP](https://metacpan.org/pod/Math::Prime::Util::GMP).

```ruby
for p in (^Inf -> lazy.grep { .is_mersenne_prime }) {
    say "2^#{p} - 1"
}
```

#### Output:
```
2^2 - 1
2^3 - 1
2^5 - 1
2^7 - 1
2^13 - 1
2^17 - 1
2^19 - 1
2^31 - 1
2^61 - 1
2^89 - 1
2^107 - 1
2^127 - 1
2^521 - 1
2^607 - 1
2^1279 - 1
2^2203 - 1
2^2281 - 1
2^3217 - 1
2^4253 - 1
2^4423 - 1
2^9689 - 1
2^9941 - 1
^C
sidef mersenne.sf  12.47s user 0.02s system 99% cpu 12.495 total
```