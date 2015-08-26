[1]: http://rosettacode.org/wiki/Runge-Kutta_method

# [Runge-Kutta method][1]

```ruby
__USE_BIGNUM__
 
func runge_kutta(yp) {
    func (t, y, δt) {
        var a = (δt * yp(t, y));
        var b = (δt * yp(t + δt/2, y + a/2));
        var c = (δt * yp(t + δt/2, y + b/2));
        var d = (δt * yp(t + δt, y + c));
        (a + 2*(b + c) + d) / 6;
    }.copy;
}
 
define δt = 0.1;
var δy = runge_kutta(func(t, y) { t * y.sqrt });
 
var(t, y) = (0, 1);
loop {
    t.is_int &&
        printf("y(%2d) = %12f ± %e\n", t, y, abs(y - ((t**2 + 4)**2 / 16)));
    t <= 10 || break;
    y += δy(t, y, δt);
    t += δt;
}
```

#### Output:
```
y( 0) =     1.000000 ± 0.000000e+00
y( 1) =     1.562500 ± 1.457219e-07
y( 2) =     3.999999 ± 9.194792e-07
y( 3) =    10.562497 ± 2.909562e-06
y( 4) =    24.999994 ± 6.234909e-06
y( 5) =    52.562489 ± 1.081970e-05
y( 6) =    99.999983 ± 1.659460e-05
y( 7) =   175.562476 ± 2.351773e-05
y( 8) =   288.999968 ± 3.156520e-05
y( 9) =   451.562459 ± 4.072316e-05
y(10) =   675.999949 ± 5.098329e-05
```