# Gauss

The `Gauss` class provides support for rational [Gaussian numbers](https://en.wikipedia.org/wiki/Gaussian_integer) and various operations on these numbers.

```ruby
Gauss(3, 4)     # represents 3+4i
```

Example:

```ruby
say Gauss(3,4)**100
say Mod(Gauss(3,4), 1000001)**100   #=> Mod(Gauss(826585, 77265), 1000001)

var a = Gauss(17,19)
var b = Gauss(43,97)

say a+b     #=> Gauss(60, 116)
say a-b     #=> Gauss(-26, -78)
say a*b     #=> Gauss(-1112, 2466)
say a/b     #=> Gauss(99/433, -32/433)
```
