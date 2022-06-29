[1]: https://rosettacode.org/wiki/Sum_of_square_and_cube_digits_of_an_integer_are_primes

# [Sum of square and cube digits of an integer are primes][1]

```ruby
1..99 -> grep { .square.digits_sum.is_prime && .cube.digits_sum.is_prime }.say
```

#### Output:
```
[16, 17, 25, 28, 34, 37, 47, 52, 64]
```
