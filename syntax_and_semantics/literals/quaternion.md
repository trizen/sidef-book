# Quaternion

The `Quaternion` class represents a [quaternion number](https://en.wikipedia.org/wiki/Quaternion) of the form `a + b*i + c*j + d*k`, where `a`, `b`, `c`, and `d` are real numbers; and `i`, `j`, and `k` are the basic quaternions.

```ruby
var a = Quaternion(1,2,3,4)
var b = Quaternion(5,6,7,8)

say a+b     #=> Quaternion(6, 8, 10, 12)
say a-b     #=> Quaternion(-4, -4, -4, -4)
say a*b     #=> Quaternion(-60, 12, 30, 24)
say b*a     #=> Quaternion(-60, 20, 14, 32)
say a/b     #=> Quaternion(35/87, 4/87, 0, 8/87)

say a**5                #=> Quaternion(3916, 1112, 1668, 2224)
say a.powmod(43, 97)    #=> Quaternion(61, 38, 57, 76)
say a.powmod(-5, 43)    #=> Quaternion(11, 22, 33, 1)
```
