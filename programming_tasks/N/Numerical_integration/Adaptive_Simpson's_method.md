[1]: https://rosettacode.org/wiki/Numerical_integration/Adaptive_Simpson's_method

# [Numerical integration/Adaptive Simpson's method][1]

```ruby
func adaptive_Simpson_quadrature(f, left, right, ε = 1e-9) {
 
    func quadrature_mid(l, lf, r, rf) {
        var mid = (l+r)/2
        var midf = f(mid)
        (mid, midf, abs(r-l)/6 * (lf + 4*midf + rf))
    }
 
    func recursive_asr(a, fa, b, fb, ε, whole, m, fm) {
        var (lm, flm, left)  = quadrature_mid(a, fa, m, fm)
        var (rm, frm, right) = quadrature_mid(m, fm, b, fb)
        var Δ = (left + right - whole)
        abs(Δ) <= 15*ε
            ? (left + right + Δ/15)
            : (__FUNC__(a, fa, m, fm, ε/2, left,  lm, flm) +
               __FUNC__(m, fm, b, fb, ε/2, right, rm, frm))
    }
 
    var (lf = f(left), rf = f(right))
    var (mid, midf, whole) = quadrature_mid(left, lf, right, rf)
    recursive_asr(left, lf, right, rf, ε, whole, mid, midf)
}
 
var (a = 0, b = 1)
var area = adaptive_Simpson_quadrature({ .sin }, a, b, 1e-15).round(-15)
say "Simpson's integration of sine from #{a} to #{b} ≈ #{area}"
```

#### Output:
```
Simpson's integration of sine from 0 to 1 ≈ 0.45969769413186
```
