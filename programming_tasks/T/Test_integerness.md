[1]: https://rosettacode.org/wiki/Test_integerness

# [Test integerness][1]

```ruby
func is_int (n, tolerance=0) {
    !!(abs(n.real.round + n.imag - n) <= tolerance)
}
 
%w(25.000000 24.999999 25.000100 -2.1e120 -5e-2 Inf NaN 5.0+0.0i 5-5i).each {|s|
    var n = Number(s)
    printf("%-10s  %-8s  %-5s\n", s,
        is_int(n),
        is_int(n, tolerance: 0.00001))
}
```

#### Output:
```
25.000000   true      true 
24.999999   false     true 
25.000100   false     false
-2.1e120    true      true 
-5e-2       false     false
Inf         false     false
NaN         false     false
5.0+0.0i    true      true 
5-5i        false     false
```