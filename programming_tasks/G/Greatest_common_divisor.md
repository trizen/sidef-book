[1]: http://rosettacode.org/wiki/Greatest_common_divisor

# [Greatest common divisor][1]

```ruby
var arr = [100, 1_000, 10_000, 20];
say Math.gcd(arr...);
```
```ruby
func gcd(a, b) {
    b.is_zero ? a.abs : gcd(b, a % b);
}
```