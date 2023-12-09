[1]: https://rosettacode.org/wiki/Greatest_common_divisor

# [Greatest common divisor][1]

### Built-in

```ruby
var arr = [100, 1_000, 10_000, 20]
say Math.gcd(arr...)
```


### Recursive Euclid algorithm

```ruby
func gcd(a, b) {
    b==0 ? a.abs : gcd(b, a % b)
}
```
