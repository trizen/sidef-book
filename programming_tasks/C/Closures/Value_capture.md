[1]: http://rosettacode.org/wiki/Closures/Value_capture

# [Closures/Value capture][1]

```ruby
var f = (
    0..9 -> map {|i| func(j){i * j}.copy }
);
 
0 ..^ 8 -> each { |j|
    say f[j].call(j);
};
```

#### Output:
```
0
1
4
9
16
25
36
49
64
```