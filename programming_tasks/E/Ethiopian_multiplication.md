[1]: https://rosettacode.org/wiki/Ethiopian_multiplication

# [Ethiopian multiplication][1]

```ruby
func double (n) { n << 1 }
func halve  (n) { n >> 1 }
func isEven (n) { n&1 == 0 }

func ethiopian_mult(a, b) {
    var r = 0
    while (a > 0) {
        r += b if !isEven(a)
        a = halve(a)
        b = double(b)
    }
    return r
}

say ethiopian_mult(17, 34)
```

#### Output:
```
578
```
