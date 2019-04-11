[1]: https://rosettacode.org/wiki/Sequence:_smallest_number_greater_than_previous_term_with_exactly_n_divisors

# [Sequence: smallest number greater than previous term with exactly n divisors][1]

```ruby
func n_divisors(n, from=1) {
    from..Inf -> first_by { .sigma0 == n }
}
 
with (1) { |from|
    say 15.of { from = n_divisors(_+1, from) }
}
```

#### Output:
```
[1, 2, 4, 6, 16, 18, 64, 66, 100, 112, 1024, 1035, 4096, 4288, 4624]
```
