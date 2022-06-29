[1]: https://rosettacode.org/wiki/Ultra_useful_primes

# [Ultra useful primes][1]

```ruby
say(" n   k")
say("----------")
 
for n in (1..13) {
    var t = 2**(2**n)
    printf("%2d   %d\n", n, {|k| t - k -> is_prob_prime }.first)
}
```

#### Output:
```
 n   k
----------
 1   1
 2   3
 3   5
 4   15
 5   5
 6   59
 7   159
 8   189
 9   569
10   105
11   1557
12   2549
13   2439
```


(takes ~20 seconds)
