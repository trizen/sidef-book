[1]: https://rosettacode.org/wiki/Matrix-exponentiation_operator

# [Matrix-exponentiation operator][1]

```ruby
class Array {
    method ** (Number n { .>= 0 }) {
        var tmp = self
        var out = self.len.of {|i| self.len.of {|j| i == j ? 1 : 0 }}
        loop {
            out = (out `mmul` tmp) if n.is_odd
            n >>= 1 || break
            tmp = (tmp `mmul` tmp)
        }
        return out
    }
}
 
var m = [[1, 2, 0],
         [0, 3, 1],
         [1, 0, 0]]
 
for order in (0..5) {
    say "### Order #{order}"
    var t = (m ** order)
    say ('  ', t.join("\n  "))
}
```

#### Output:
```
### Order 0
  [1, 0, 0]
  [0, 1, 0]
  [0, 0, 1]
### Order 1
  [1, 2, 0]
  [0, 3, 1]
  [1, 0, 0]
### Order 2
  [1, 8, 2]
  [1, 9, 3]
  [1, 2, 0]
### Order 3
  [3, 26, 8]
  [4, 29, 9]
  [1, 8, 2]
### Order 4
  [11, 84, 26]
  [13, 95, 29]
  [3, 26, 8]
### Order 5
  [37, 274, 84]
  [42, 311, 95]
  [11, 84, 26]
```