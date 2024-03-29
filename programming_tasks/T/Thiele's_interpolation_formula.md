[1]: https://rosettacode.org/wiki/Thiele's_interpolation_formula

# [Thiele's interpolation formula][1]

```ruby
func thiele(x, y) {
    var ρ = {|i| [y[i]]*(y.len-i) }.map(^y)
 
    for i in ^(ρ.end) {
        ρ[i][1] = ((x[i] - x[i+1]) / (ρ[i][0] - ρ[i+1][0]))
    }
    for i (2 .. ρ.end) {
        for j (0 .. ρ.end-i) {
            ρ[j][i] = (((x[j]-x[j+i]) / (ρ[j][i-1]-ρ[j+1][i-1])) + ρ[j+1][i-2])
        }
    }
 
    var ρ0 = ρ[0]
 
    func t(xin) {
        var a = 0
        for i (ρ0.len ^.. 2) {
            a = ((xin - x[i-1]) / (ρ0[i] - ρ0[i-2] + a))
        }
        y[0] + ((xin-x[0]) / (ρ0[1]+a))
    }
    return t
}
 
# task 1: build 32 row trig table
var xVal = {|k| k * 0.05 }.map(^32)
var tSin = xVal.map { .sin }
var tCos = xVal.map { .cos }
var tTan = xVal.map { .tan }
 
# task 2: define inverses
var iSin = thiele(tSin, xVal)
var iCos = thiele(tCos, xVal)
var iTan = thiele(tTan, xVal)
 
# task 3: demonstrate identities
say 6*iSin(0.5)
say 3*iCos(0.5)
say 4*iTan(1)
```

#### Output:
```
3.14159265358979323846438729976818601771260734312
3.14159265358979323846157620314930763214337987744
3.14159265358979323846264318595256260456200366896
```
