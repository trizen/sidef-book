[1]: https://rosettacode.org/wiki/Ramanujan's_constant

# [Ramanujan's constant][1]

```ruby
func ramanujan_const(x, decimals=32) {
    local Num!PREC = *"#{4*round((Num.pi*√x)/log(10) + decimals + 1)}"
    exp(Num.pi * √x) -> round(-decimals).to_s
}
 
var decimals = 100
printf("Ramanujan's constant to #{decimals} decimals:\n%s\n\n",
     ramanujan_const(163, decimals))
 
say "Heegner numbers yielding 'almost' integers:"
[19, 96, 43, 960, 67, 5280, 163, 640320].each_slice(2, {|h,x|
    var c = ramanujan_const(h, 32)
    var n = (x**3 + 744)
    printf("%3s: %51s ≈ %18s (diff: %s)\n", h, c, n, n-Num(c))
})
```

#### Output:
```
Ramanujan's constant to 100 decimals:
262537412640768743.9999999999992500725971981856888793538563373369908627075374103782106479101186073129511813461860645042

Heegner numbers yielding 'almost' integers:
 19:             885479.77768015431949753789348171962682 ≈             885480 (diff: 0.22231984568050246210651828037318)
 43:          884736743.99977746603490666193746207858538 ≈          884736744 (diff: 0.00022253396509333806253792141462)
 67:       147197952743.99999866245422450682926131257863 ≈       147197952744 (diff: 0.00000133754577549317073868742137)
163: 262537412640768743.99999999999925007259719818568888 ≈ 262537412640768744 (diff: 0.00000000000074992740280181431112)
```
