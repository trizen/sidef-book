[1]: https://rosettacode.org/wiki/Order_two_numerical_lists

# [Order two numerical lists][1]

Built-in, via the comparison operator (\`&lt;=&gt;\`):

```ruby
func ordered(a, b) {
    (a <=> b) < 0
}
 
for p in [
    Pair([1,2,4], [1,2,4]),
    Pair([1,2,4], [1,2]  ),
    Pair([1,2],   [1,2,4]),
] {
    var a = p.first
    var b = p.second
    var before = ordered(a, b)
    say "#{a} comes before #{b} : #{before}"
}
```

#### Output:
```
[1, 2, 4] comes before [1, 2, 4] : false
[1, 2, 4] comes before [1, 2] : false
[1, 2] comes before [1, 2, 4] : true
```