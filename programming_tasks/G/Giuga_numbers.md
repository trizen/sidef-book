[1]: https://rosettacode.org/wiki/Giuga_numbers

# [Giuga numbers][1]

```ruby
4..Inf `by` 2 -> lazy.grep {|n|
    n.factor.all {|p| p `divides` (n/p - 1) }
}.first(4).say
```

#### Output:
```
[30, 858, 1722, 66198]
```
