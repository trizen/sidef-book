[1]: https://rosettacode.org/wiki/Prime_triplets

# [Prime triplets][1]

```ruby
say "Values of p such that (p, p+2, p+6) are all prime:"
5500.primes.grep{|p| all_prime(p+2, p+6) }.say
```

#### Output:
```
Values of p such that (p, p+2, p+6) are all prime:
[5, 11, 17, 41, 101, 107, 191, 227, 311, 347, 461, 641, 821, 857, 881, 1091, 1277, 1301, 1427, 1481, 1487, 1607, 1871, 1997, 2081, 2237, 2267, 2657, 2687, 3251, 3461, 3527, 3671, 3917, 4001, 4127, 4517, 4637, 4787, 4931, 4967, 5231, 5477]
```
