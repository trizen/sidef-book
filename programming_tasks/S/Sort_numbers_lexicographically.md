[1]: https://rosettacode.org/wiki/Sort_numbers_lexicographically

# [Sort numbers lexicographically][1]

```ruby
func lex_order (n) {
    [range(1, n, n.sgn)...].sort_by { Str(_) }
}
 
[13, 21, -22].each {|n|
    printf("%4s: %s\n", n, lex_order(n))
}
```

#### Output:
```
  13: [1, 10, 11, 12, 13, 2, 3, 4, 5, 6, 7, 8, 9]
  21: [1, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 2, 20, 21, 3, 4, 5, 6, 7, 8, 9]
 -22: [-1, -10, -11, -12, -13, -14, -15, -16, -17, -18, -19, -2, -20, -21, -22, -3, -4, -5, -6, -7, -8, -9, 0, 1]
```