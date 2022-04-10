[1]: https://rosettacode.org/wiki/Find_squares_n_where_n%2B1_is_prime

# [Find squares n where n+1 is prime][1]

```ruby
1..1000.isqrt -> map { _**2 }.grep { is_prime(_+1) }.say
```

#### Output:
```
[1, 4, 16, 36, 100, 196, 256, 400, 576, 676]
```
