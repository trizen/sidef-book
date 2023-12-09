[1]: https://rosettacode.org/wiki/Averages/Arithmetic_mean

# [Averages/Arithmetic mean][1]

```ruby
func avg(Array list) {
    list.len > 0 || return 0
    list.sum / list.len
}

say avg([Inf, Inf])
say avg([3,1,4,1,5,9])
say avg([1e+20, 3, 1, 4, 1, 5, 9, -1e+20])
say avg([10, 9, 8, 7, 6, 5, 4, 3, 2, 1, 0, 0, 0, 0, 0.11])
say avg([10, 20, 30, 40, 50, -100, 4.7, -1100])
```

#### Output:
```
Inf
3.83333333333333333333333333333333
2.875
3.674
-130.6625
```
