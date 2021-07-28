[1]: https://rosettacode.org/wiki/Self_numbers

# [Self numbers][1]

Algorithm by David A. Corneth (OEIS: A003052).

```ruby
func is_self_number(n) {
 
    if (n < 30) {
        return (((n < 10) && (n.is_odd)) || (n == 20))
    }
 
    var qd = (1 + n.ilog10)
    var r  = (1 + (n-1)%9)
    var h  = (r + 9*(r%2))/2
    var ld = 10
 
    while (h + 9*qd >= n%ld) {
        ld *= 10
    }
 
    var vs = idiv(n, ld).sumdigits
    n %= ld
 
    0..qd -> none { |i|
        vs + sumdigits(n - h - 9*i) == (h + 9*i)
    }
}
 
say is_self_number.first(50).join(' ')
```

#### Output:
```
1 3 5 7 9 20 31 42 53 64 75 86 97 108 110 121 132 143 154 165 176 187 198 209 211 222 233 244 255 266 277 288 299 310 312 323 334 345 356 367 378 389 400 411 413 424 435 446 457 468
```


Simpler algorithm (by M. F. Hasler):

```ruby
func is_self_number(n) {
    1..min(n>>1, 9*n.len) -> none {|i| sumdigits(n-i) == i } && (n > 0)
}
```
