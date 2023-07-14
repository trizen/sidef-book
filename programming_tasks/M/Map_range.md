[1]: https://rosettacode.org/wiki/Map_range

# [Map range][1]

```ruby
func map_range(a, b, x) {
    var (a1, a2, b1, b2) = (a.bounds, b.bounds)
    x-a1 * b2-b1 / a2-a1 + b1
}
 
var a = 0..10
var b = -1..0
 
a.each { |x|
    say "#{x} maps to #{map_range(a, b, x)}"
}
```

#### Output:
```
0 maps to -1
1 maps to -0.9
2 maps to -0.8
3 maps to -0.7
4 maps to -0.6
5 maps to -0.5
6 maps to -0.4
7 maps to -0.3
8 maps to -0.2
9 maps to -0.1
10 maps to 0
```
