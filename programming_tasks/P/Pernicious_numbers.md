[1]: https://rosettacode.org/wiki/Pernicious_numbers

# [Pernicious numbers][1]

```ruby
func is_pernicious(n) {
    n.sumdigits(2).is_prime
}

say is_pernicious.first(25).join(' ')
say is_pernicious.grep(888_888_877..888_888_888).join(' ')
```

#### Output:
```
3 5 6 7 9 10 11 12 13 14 17 18 19 20 21 22 24 25 26 28 31 33 34 35 36
888888877 888888878 888888880 888888883 888888885 888888886
```
