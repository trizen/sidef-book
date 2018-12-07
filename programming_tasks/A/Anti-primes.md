[1]: https://rosettacode.org/wiki/Anti-primes

# [Anti-primes][1]

Using the built-in *Number.sigma0* method to count the number of divisors.

```ruby
say with (0) {|max|
    1..Inf -> lazy.grep { (.sigma0 > max) && (max = .sigma0) }.first(20)
}
```

#### Output:
```
[1, 2, 4, 6, 12, 24, 36, 48, 60, 120, 180, 240, 360, 720, 840, 1260, 1680, 2520, 5040, 7560]
```