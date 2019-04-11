[1]: https://rosettacode.org/wiki/Sequence:_smallest_number_with_exactly_n_divisors

# [Sequence: smallest number with exactly n divisors][1]

```ruby
func n_divisors(n) {
    1..Inf -> first_by { .sigma0 == n }
}
 
say 15.of { n_divisors(_+1) }
```

#### Output:
```
[1, 2, 4, 6, 16, 12, 64, 24, 36, 48, 1024, 60, 4096, 192, 144]
```
