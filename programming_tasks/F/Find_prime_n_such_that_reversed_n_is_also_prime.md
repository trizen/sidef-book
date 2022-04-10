[1]: https://rosettacode.org/wiki/Find_prime_n_such_that_reversed_n_is_also_prime

# [Find prime n such that reversed n is also prime][1]

```ruby
say primes(500).grep { .reverse.is_prime }
```

#### Output:
```
[2, 3, 5, 7, 11, 13, 17, 31, 37, 71, 73, 79, 97, 101, 107, 113, 131, 149, 151, 157, 167, 179, 181, 191, 199, 311, 313, 337, 347, 353, 359, 373, 383, 389]
```
