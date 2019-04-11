[1]: https://rosettacode.org/wiki/Sequence:_nth_number_with_exactly_n_divisors

# [Sequence: nth number with exactly n divisors][1]

```ruby
func f(n {.is_prime}) {
    n.prime**(n-1)
}
 
func f(n) {
    n.th { .sigma0 == n }
}
 
say 20.of { f(_+1) }
```

#### Output:
```
[1, 3, 25, 14, 14641, 44, 24137569, 70, 1089, 405, 819628286980801, 160, 22563490300366186081, 2752, 9801, 462, 21559177407076402401757871041, 1044, 740195513856780056217081017732809, 1520]
```
