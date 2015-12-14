[1]: http://rosettacode.org/wiki/Modular_inverse

# [Modular inverse][1]

Built-in:

```ruby
say 42.modinv(2017)
```


Algorithm implementation:

```ruby
func invmod(a, n) {
  var (t, nt, r, nr) = (0, 1, n, a % n)
  while (nr != 0) {
    var quot = int((r - (r % nr)) / nr);
    (nt, t) = (t - quot*nt, nt);
    (nr, r) = (r - quot*nr, nr);
  }
  r > 1 && return()
  t < 0 && (t += n)
  t
}
 
say invmod(42, 2017)
```

#### Output:
```
1969
```