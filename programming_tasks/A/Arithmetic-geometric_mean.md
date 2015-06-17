[1]: http://rosettacode.org/wiki/Arithmetic-geometric_mean

# [Arithmetic-geometric mean][1]

```ruby
func agm(a, g) {
    loop {
        var x = [a+g / 2, Math.sqrt(a*g)];
        x == [a, g] && return a;
        x » (\a, \g);
    }
}
 
say agm(1, 1/Math.sqrt(2));
```

#### Output:
```
0.8472130847939790866064991234821916364814
```