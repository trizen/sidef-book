[1]: https://rosettacode.org/wiki/Neighbour_primes

# [Neighbour primes][1]

```ruby
500.primes.grep {|p| p * p.next_prime + 2 -> is_prime }.say
```

#### Output:
```
[3, 5, 7, 13, 19, 67, 149, 179, 229, 239, 241, 269, 277, 307, 313, 397, 401, 419, 439, 487]
```
