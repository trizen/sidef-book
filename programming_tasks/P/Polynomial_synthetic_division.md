[1]: https://rosettacode.org/wiki/Polynomial_synthetic_division

# [Polynomial synthetic division][1]

```ruby
func extended_synthetic_division(dividend, divisor) {
    var end = divisor.end
    var out = dividend.clone
    var normalizer = divisor[0]
 
    for i in ^(dividend.len - end) {
        out[i] /= normalizer
        var coef = out[i]
        if (coef != 0) {
            for j in (1 .. end) {
                out[i+j] += -(divisor[j] * coef)
            }
        }
    }
 
    var remainder = out.splice(-end)
    var quotient = out
 
    return(quotient, remainder)
}
 
var (n, d) = ([1, -12, 0, -42], [1, -3])
print("  %s / %s =" % (n, d))
print(" %s remainder %s\n" % extended_synthetic_division(n, d))
```

#### Output:
```
  [1, -12, 0, -42] / [1, -3] = [1, -9, -27] remainder [-123]
```