[1]: https://rosettacode.org/wiki/Safe_and_Sophie_Germain_primes

# [Safe and Sophie Germain primes][1]

```ruby
^Inf -> lazy.grep{|p| all_prime(p, 2*p + 1) }.first(50).slices(10).each{
    .join(', ').say
}
```

#### Output:
```
2, 3, 5, 11, 23, 29, 41, 53, 83, 89
113, 131, 173, 179, 191, 233, 239, 251, 281, 293
359, 419, 431, 443, 491, 509, 593, 641, 653, 659
683, 719, 743, 761, 809, 911, 953, 1013, 1019, 1031
1049, 1103, 1223, 1229, 1289, 1409, 1439, 1451, 1481, 1499
```
