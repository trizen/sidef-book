[1]: http://rosettacode.org/wiki/Arbitrary-precision_integers_(included)

# [Arbitrary-precision integers (included)][1]

```ruby
var x = 5**(4**(3**2))
var y = x.to_s
printf("5**4**3**2 = %s...%s and has %i digits\n", y.first(20), y.last(20), y.len)
```

#### Output:
```
5**4**3**2 = 62060698786608744707...92256259918212890625 and has 183231 digits
```
