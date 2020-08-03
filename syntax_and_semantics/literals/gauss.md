# Gauss

This class provides support for rational [Gaussian numbers](https://en.wikipedia.org/wiki/Gaussian_integer) and various operations on these numbers.

```ruby
Gauss(3, 4)     # represents 3+4i
```

Example:

```ruby
say Gauss(3,4)**100
say Mod(Gauss(3,4), 1000001)**100   #=> Mod((826585, 77265), 1000001)

var a = Gauss(17,19)
var b = Gauss(43,97)

say a+b     #=> (60, 116)
say a-b     #=> (-26, -78)
say a*b     #=> (-1112, 2466)
say a/b     #=> (99/433, -32/433)
```
