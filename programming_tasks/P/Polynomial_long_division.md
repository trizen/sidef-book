[1]: https://rosettacode.org/wiki/Polynomial_long_division

# [Polynomial long division][1]

```ruby
func poly_long_div(rn, rd) {
 
    var n = rn.map{_}
    var gd = rd.len
 
    if (n.len >= gd) {
        return(gather {
            while (n.len >= gd) {
                var piv = n[0]/rd[0]
                take(piv)
                { |i|
                    n[i] -= (rd[i] * piv)
                } << ^(n.len `min` gd)
                n.shift
            }
        }, n)
    }
 
    return([0], rn)
}
```


Example:

```ruby
func poly_print(c) {
    var l = c.len
    c.each_kv {|i, n|
        print n
        print("x^", (l - i - 1), " + ") if (i < l-1)
    }
    print "\n"
}
 
var poly = [
    Pair([1,-12,0,-42],  [1, -3]),
    Pair([1,-12,0,-42], [1,1,-3]),
    Pair(      [1,3,2],    [1,1]),
    Pair( [1,-4,6,5,3],  [1,2,1]),
]
 
poly.each { |pair|
    var (q, r) = poly_long_div(pair.first, pair.second)
    poly_print(q)
    poly_print(r)
    print "\n"
}
```

#### Output:
```
1x^2 + -9x^1 + -27
-123

1x^1 + -13
16x^1 + -81

1x^1 + 2
0

1x^2 + -6x^1 + 17
-23x^1 + -14
```
