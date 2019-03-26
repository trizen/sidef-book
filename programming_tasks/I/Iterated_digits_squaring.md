[1]: https://rosettacode.org/wiki/Iterated_digits_squaring

# [Iterated digits squaring][1]

```ruby
func digit_square_sum_iter(n) is cached {
 
    if ((n == 1) || (n == 89)) {
        return n
    }
 
    __FUNC__(n.digits.sum { .sqr })
}
 
say (1..1e6 -> count_by { digit_square_sum_iter(_) == 89 })
```

#### Output:
```
856929
```