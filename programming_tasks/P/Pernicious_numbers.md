[1]: http://rosettacode.org/wiki/Pernicious_numbers

# [Pernicious numbers][1]

```ruby
func is_pernicious(n) {
    var c = 2693408940  # primes < 32 as set bits
    while (n > 0) { c >>= 1; n &= (n - 1) }
    c & 1
}
 
var (i, *p) = 0
while (p.len < 25) {
    p << i if is_pernicious(i)
    ++i
}
 
say p.join(' ')
 
var (i, *p) = 888888877
while (i < 888888888) {
    p << i if is_pernicious(i)
    ++i
}
 
say p.join(' ')
```

#### Output:
```
3 5 6 7 9 10 11 12 13 14 17 18 19 20 21 22 24 25 26 28 31 33 34 35 36
888888877 888888878 888888880 888888883 888888885 888888886
```
