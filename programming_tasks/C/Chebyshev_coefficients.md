[1]: http://rosettacode.org/wiki/Chebyshev_coefficients

# [Chebyshev coefficients][1]

```ruby
func chebft (callback, a, b, n) {
 
    var bma = (0.5 * b-a);
    var bpa = (0.5 * b+a);
 
    var pi_n = ((0..(n-1) »+» 0.5) »*» (Math::PI / n));
    var f = (pi_n »cos»() »*» bma »+» bpa «call« callback);
    var sums = (0..(n-1) «run« {|i| f »*« ((pi_n »*» i) »cos»()) «+» });
 
    sums »*» (2/n);
}
 
chebft(func(v){v.cos}, 0, 1, 10).each { |v|
    say ("%+.10e" % v);
}
```

#### Output:
```
+1.6471694754e+00
-2.3229937162e-01
-5.3715114622e-02
+2.4582352670e-03
+2.8211905743e-04
-7.7222291558e-06
-5.8985564522e-07
+1.1521427333e-08
+6.5963000351e-10
-1.0022591709e-11
```
