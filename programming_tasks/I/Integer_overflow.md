[1]: http://rosettacode.org/wiki/Integer_overflow

# [Integer overflow][1]

Sidef has unlimited precision integers.

```ruby
var (a, b, c) = (9223372036854775807, 5000000000000000000, 3037000500)
[-(-a - 1), b + b, -a - a, c * c, (-a - 1)/-1].each { say _ }
```

#### Output:
```
9223372036854775808
10000000000000000000
-18446744073709551614
9223372037000250000
9223372036854775808
```
