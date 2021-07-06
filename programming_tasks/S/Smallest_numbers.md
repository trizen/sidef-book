[1]: https://rosettacode.org/wiki/Smallest_numbers

# [Smallest numbers][1]

```ruby
0..50 -> map {|n| 1..Inf -> first {|k| Str(k**k).contains(n) } }.say
```

#### Output:
```
[9, 1, 3, 5, 2, 4, 4, 3, 7, 9, 10, 11, 5, 19, 22, 26, 8, 17, 16, 19, 9, 8, 13, 7, 17, 4, 17, 3, 11, 18, 13, 5, 23, 17, 18, 7, 17, 15, 9, 18, 16, 17, 9, 7, 12, 28, 6, 23, 9, 24, 23]
```
