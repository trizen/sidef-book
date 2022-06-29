[1]: https://rosettacode.org/wiki/Strange_unique_prime_triplets

# [Strange unique prime triplets][1]

```ruby
for n in (30, 1000) {
    var triplets = []
    combinations(n.primes, 3, {|*a|
        triplets << a if a.sum.is_prime
    })
    if (n == 30) {
        say "Unique prime triplets (p,q,r) <= #{n} such that p+q+r is prime:"
        triplets.slices(6).each{.join(' ').say}
    }
    printf("Found %d strange unique prime triplets up to %s.\n", triplets.len, n)
}
```

#### Output:
```
Unique prime triplets (p,q,r) <= 30 such that p+q+r is prime:
[3, 5, 11] [3, 5, 23] [3, 5, 29] [3, 7, 13] [3, 7, 19] [3, 11, 17]
[3, 11, 23] [3, 11, 29] [3, 17, 23] [5, 7, 11] [5, 7, 17] [5, 7, 19]
[5, 7, 29] [5, 11, 13] [5, 13, 19] [5, 13, 23] [5, 13, 29] [5, 17, 19]
[5, 19, 23] [5, 19, 29] [7, 11, 13] [7, 11, 19] [7, 11, 23] [7, 11, 29]
[7, 13, 17] [7, 13, 23] [7, 17, 19] [7, 17, 23] [7, 17, 29] [7, 23, 29]
[11, 13, 17] [11, 13, 19] [11, 13, 23] [11, 13, 29] [11, 17, 19] [11, 19, 23]
[11, 19, 29] [13, 17, 23] [13, 17, 29] [13, 19, 29] [17, 19, 23] [19, 23, 29]
Found 42 strange unique prime triplets up to 30.
Found 241580 strange unique prime triplets up to 1000.
```
