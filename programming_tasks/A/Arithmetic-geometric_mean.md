[1]: https://rosettacode.org/wiki/Arithmetic-geometric_mean

# [Arithmetic-geometric mean][1]

```ruby
func agm(a, g) {
    loop {
        var (a1, g1) = ((a+g)/2, sqrt(a*g))
        [a1,g1] == [a,g] && return a
        (a, g) = (a1, g1)
    }
}

say agm(1, 1/sqrt(2))
```

#### Output:
```
0.84721308479397908660649912348219163648
```
