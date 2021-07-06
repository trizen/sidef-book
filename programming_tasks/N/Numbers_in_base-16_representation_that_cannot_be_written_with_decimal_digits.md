[1]: https://rosettacode.org/wiki/Numbers_in_base-16_representation_that_cannot_be_written_with_decimal_digits

# [Numbers in base-16 representation that cannot be written with decimal digits][1]

Simple solution:

```ruby
1..500 -> grep { .digits(16).min >= 10 }.say
```


More efficient approach:

```ruby
func generate_from_prefix(limit, p, base, digits) {
 
    var seq = [p]
 
    for d in (digits) {
        var t = [d, p...]
        if (t.digits2num(base) <= limit) {
            seq << __FUNC__(limit, t, base, digits)...
        }
    }
 
    return seq
}
 
func numbers_with_non_decimal_digits(limit, base = 10) {
    var digits = @(10..^base)
    digits.map  {|p| generate_from_prefix(limit, [p], base, digits)... }\
          .map  {|t| digits2num(t, base) }\
          .sort
}
 
say numbers_with_non_decimal_digits(500, 16)
```

#### Output:
```
[10, 11, 12, 13, 14, 15, 170, 171, 172, 173, 174, 175, 186, 187, 188, 189, 190, 191, 202, 203, 204, 205, 206, 207, 218, 219, 220, 221, 222, 223, 234, 235, 236, 237, 238, 239, 250, 251, 252, 253, 254, 255]
```
