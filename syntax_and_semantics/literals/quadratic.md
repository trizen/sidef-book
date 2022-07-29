# Quadratic

The `Quadratic` class represents a [quadratic integer](https://en.wikipedia.org/wiki/Quadratic_integer) of the form: `a + b*sqrt(w)`.

```ruby
var x = Quadratic(3, 4, 5)  # represents: 3 + 4*sqrt(5)
var y = Quadratic(6, 1, 2)  # represents: 6 + sqrt(2)

say x**10       #=> Quadratic(29578174649, 13203129720, 5)
say y**10       #=> Quadratic(253025888, 176008128, 2)

say x.powmod(100, 97)   #=> Quadratic(83, 42, 5)
say y.powmod(100, 97)   #=> Quadratic(83, 39, 2)
```
