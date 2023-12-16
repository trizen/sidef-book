[1]: https://rosettacode.org/wiki/CORDIC

# [CORDIC][1]

```ruby
func CORDIC(a) {
    var (k, x, y) = (0, 1, 0)
    var PoT = %n(1, 0.1, 0.01, 0.001, 0.0001, 0.00001)
    var Tbl = %n(7.853981633e-1 9.966865249e-2 9.999666686e-3 9.999996666e-4 9.999999966e-5 9.999999999e-6 0)

    for (true; a > 1e-5; a -= Tbl[k]) {
        while (a < Tbl[k]) { ++k }
        (x,y) = (x - PoT[k]*y, y + PoT[k]*x)
    }
    x / hypot(x,y)
}

print("Angle    CORDIC       Cosine       Error\n")
for angle in (%n(-9 0 1.5 6)) {
    var cordic = CORDIC(angle.abs)
    printf("%4.1f %12.8f %12.8f %12.8f\n", angle, cordic, cos(angle), cos(angle) - cordic)
}
```

#### Output:
```
Angle    CORDIC       Cosine       Error
-9.0  -0.91112769  -0.91113026  -0.00000257
 0.0   1.00000000   1.00000000   0.00000000
 1.5   0.07073880   0.07073720  -0.00000160
 6.0   0.96016761   0.96017029   0.00000268
```
