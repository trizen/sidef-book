[1]: https://rosettacode.org/wiki/Repunit_primes

# [Repunit primes][1]

```ruby
var limit = 1000
 
say "Repunit prime digits (up to #{limit}) in:"
 
for n in (2..20) {
    printf("Base %2d: %s\n", n,
        {|k| is_prime((n**k - 1) / (n-1)) }.grep(1..limit))
}
```

#### Output:
```
Base  2: [2, 3, 5, 7, 13, 17, 19, 31, 61, 89, 107, 127, 521, 607]
Base  3: [3, 7, 13, 71, 103, 541]
Base  4: [2]
Base  5: [3, 7, 11, 13, 47, 127, 149, 181, 619, 929]
Base  6: [2, 3, 7, 29, 71, 127, 271, 509]
Base  7: [5, 13, 131, 149]
Base  8: [3]
Base  9: []
Base 10: [2, 19, 23, 317]
Base 11: [17, 19, 73, 139, 907]
Base 12: [2, 3, 5, 19, 97, 109, 317, 353, 701]
Base 13: [5, 7, 137, 283, 883, 991]
Base 14: [3, 7, 19, 31, 41]
Base 15: [3, 43, 73, 487]
Base 16: [2]
Base 17: [3, 5, 7, 11, 47, 71, 419]
Base 18: [2]
Base 19: [19, 31, 47, 59, 61, 107, 337]
Base 20: [3, 11, 17]
```
