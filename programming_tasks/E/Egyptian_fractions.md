[1]: http://rosettacode.org/wiki/Egyptian_fractions

# [Egyptian fractions][1]

```ruby
func ef(fr) {
  var ans = []
  if (fr >= 1) {
    return([fr]) if (fr.is_int)
    var intfr = fr.to_i
    ans << intfr
    fr -= intfr
  }
  var (x, y) = fr.nude
  while (x != 1) {
    ans << fr.inv.ceil.inv
    fr = ((-y % x) / y*fr.inv.ceil)
    (x, y) = fr.nude
  }
  ans << fr
  return ans
}
 
for fr in [43/48, 5/121, 2014/59] {
  "%s => %s\n".printf(fr.as_rat, ef(fr).map{.as_rat}.join(' + '))
}
 
var lenmax = (var denommax = [0])
for b in (2 .. 99) {
  for a in (1 .. b-1) {
    var fr = a/b
    var e = ef(fr)
    var (elen, edenom) = (e.length, e[-1].denominator)
    lenmax = [elen, fr] if (elen > lenmax[0])
    denommax = [edenom, fr] if (edenom > denommax[0])
  }
}
 
"Term max is %s with %i terms\n".printf(lenmax[1].as_rat, lenmax[0])
"Denominator max is %s with %i digits\n".printf(denommax[1].as_rat, denommax[0].size)
say denommax[0]
```

#### Output:
```
43/48 => 1/2 + 1/3 + 1/16
5/121 => 1/25 + 1/757 + 1/763309 + 1/873960180913 + 1/1527612795642093418846225
2014/59 => 34 + 1/8 + 1/95 + 1/14947 + 1/670223480
Term max is 44/53 with 8 terms
Denominator max is 8/97 with 150 digits
579504587067542801713103191859918608251030291952195423583529357653899418686342360361798689053273749372615043661810228371898539583862011424993909789665
```
