[1]: https://rosettacode.org/wiki/Positive_decimal_integers_with_the_digit_1_occurring_exactly_twice

# [Positive decimal integers with the digit 1 occurring exactly twice][1]

```ruby
say (1..1000 -> grep { .digits.count { _ == 1 } == 2 })
```

#### Output:
```
[11, 101, 110, 112, 113, 114, 115, 116, 117, 118, 119, 121, 131, 141, 151, 161, 171, 181, 191, 211, 311, 411, 511, 611, 711, 811, 911]
```
