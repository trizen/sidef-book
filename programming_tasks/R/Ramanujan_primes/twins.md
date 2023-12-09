[1]: https://rosettacode.org/wiki/Ramanujan_primes/twins

# [Ramanujan primes/twins][1]

```ruby
require('ntheory')

var rp = %S<ntheory>.ramanujan_primes(%S<ntheory>.nth_ramanujan_prime(1e6))
for limit in ([1e5, 1e6]) {
    printf("The %sth Ramanujan prime is %s\n", limit.commify, rp[limit-1].commify)
    printf("There are %s twins in the first %s Ramanujan primes.\n\n",
        ^(limit-1) -> count {|i| rp[i+1] == rp[i]+2 }.commify, limit.commify)
}
```

#### Output:
```
The 100,000th Ramanujan prime is 2,916,539
There are 8,732 twins in the first 100,000 Ramanujan primes.

The 1,000,000th Ramanujan prime is 34,072,993
There are 74,973 twins in the first 1,000,000 Ramanujan primes.
```
