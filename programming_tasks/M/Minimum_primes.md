[1]: https://rosettacode.org/wiki/Minimum_primes

# [Minimum primes][1]

```ruby
var lists = [
    [ 5,45,23,21,67],
    [43,22,78,46,38],
    [ 9,98,12,54,53],
]
 
say lists.zip.map { next_prime(.max - 1) }
```

#### Output:
```
[43, 101, 79, 59, 67]
```
