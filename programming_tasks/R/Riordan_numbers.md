[1]: https://rosettacode.org/wiki/Riordan_numbers

# [Riordan numbers][1]

```ruby
func riordan(n) is cached {
    return 1 if (n == 0)
    return 0 if (n == 1)
    (n-1) * (2*__FUNC__(n-1) + 3*__FUNC__(n-2)) / (n+1)
}

say 32.of(riordan)

for n in (1e3, 1e4) {
    var s = Str(riordan(n-1))
    say "#{'%6s' % n.commify}th term: #{s.first(20)}..#{s.last(20)} (#{s.len} digits)"
}
```

#### Output:
```
[1, 0, 1, 1, 3, 6, 15, 36, 91, 232, 603, 1585, 4213, 11298, 30537, 83097, 227475, 625992, 1730787, 4805595, 13393689, 37458330, 105089229, 295673994, 834086421, 2358641376, 6684761125, 18985057351, 54022715451, 154000562758, 439742222071, 1257643249140]
 1,000th term: 51077756867821111314..79942013897484633052 (472 digits)
10,000th term: 19927418577260688844..71395322020211157137 (4765 digits)
```
