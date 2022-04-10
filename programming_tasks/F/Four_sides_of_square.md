[1]: https://rosettacode.org/wiki/Four_sides_of_square

# [Four sides of square][1]

```ruby
var n = 5
 
[n.of(1), (n-2).of([1, (n-2).of(0)..., 1])..., n.of(1)].each {|row|
    say row.join(' ')
}
```

#### Output:
```
1 1 1 1 1
1 0 0 0 1
1 0 0 0 1
1 0 0 0 1
1 1 1 1 1
```
