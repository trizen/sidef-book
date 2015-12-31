[1]: http://rosettacode.org/wiki/Arithmetic-geometric_mean

# [Arithmetic-geometric mean][1]

```ruby
func agm(a, g) {
    loop {
        var x = [float(a+g / 2), sqrt(a*g)];
        x == [a, g] && return a;
        (a, g) = x...;
    }
}

say agm(1, 1/sqrt(2));
```

#### Output:
```
0.84721308479397908660649912348219163648
```
