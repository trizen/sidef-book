[1]: https://rosettacode.org/wiki/First_perfect_square_in_base_n_with_n_unique_digits

# [First perfect square in base n with n unique digits][1]

```ruby
func first_square(b) {
 
    var start = [1, 0, (2..^b)...].flip.map_kv{|k,v| v * b**k }.sum.isqrt
 
    start..Inf -> first_by {|k|
        k.sqr.digits(b).freq.len == b
    }.sqr
}
 
for b in (2..16) {
    var s = first_square(b)
    printf("Base %2d: %10s² == %s\n", b, s.isqrt.base(b), s.base(b))
}
```

#### Output:
```
Base  2:         10² == 100
Base  3:         22² == 2101
Base  4:         33² == 3201
Base  5:        243² == 132304
Base  6:        523² == 452013
Base  7:       1431² == 2450361
Base  8:       3344² == 13675420
Base  9:      11642² == 136802574
Base 10:      32043² == 1026753849
Base 11:     111453² == 1240a536789
Base 12:     3966b9² == 124a7b538609
Base 13:    3828943² == 10254773ca86b9
Base 14:    3a9db7c² == 10269b8c57d3a4
Base 15:   1012b857² == 102597bace836d4
Base 16:   404a9d9b² == 1025648cfea37bd9
```
