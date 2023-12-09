[1]: https://rosettacode.org/wiki/Jensen's_Device

# [Jensen's Device][1]

```ruby
var i
func sum (i, lo, hi, term) {
    var temp = 0
    for (*i = lo; *i <= hi; (*i)++) {
        temp += term.run
    }
    return temp
}
say sum(\i, 1, 100, { 1 / i })
```

#### Output:
```
5.18737751763962026080511767565825315790897212671
```
