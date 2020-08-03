# Mod

This class represents a modular operation, similar to PARI/GP's built-in `Mod(a,m)` class.

```ruby
Mod(3, 4)       # represents 3 mod 4
```

Example:


```ruby
var a = Mod(13, 19)

a += 15             # Mod(9, 19)
a *= 99             # Mod(17, 19)
a /= 17             # Mod(1, 19)

say a               # Mod(1, 19)
say (a == 1)        # true

a -= 43             # Mod(15, 19)

say a**42           # Mod(11, 19)
say a**(-1)         # Mod(14, 19)
say sqrt(a+1)       # Mod(4, 19)

say chinese(Mod(43, 19), Mod(13, 41))   # Mod(423, 779)
```
