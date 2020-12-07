[1]: https://rosettacode.org/wiki/Approximate_equality

# [Approximate equality][1]

Two values can be compared for approximate equality by using the built-in operator **≅**, available in ASCII as **=~=**, which does approximate comparison by rounding both operands at **(PREC&gt;&gt;2)-1** decimals. However, by default, Sidef uses a floating-point precision of 192 bits.

```ruby
[
    100000000000000.01, 100000000000000.011,
    100.01, 100.011,
    10000000000000.001 / 10000.0, 1000000000.0000001000,
    0.001, 0.0010000001,
    0.000000000000000000000101, 0.0,
    sqrt(2) * sqrt(2), 2.0,
    -sqrt(2) * sqrt(2), -2.0,
    sqrt(-2) * sqrt(-2), -2.0,
    cbrt(3)**3, 3,
    cbrt(-3)**3, -3,
    100000000000000003.0, 100000000000000004.0,
    3.14159265358979323846, 3.14159265358979324
].each_slice(2, {|a,b|
    say ("#{a} ≅ #{b}: ", a ≅ b)
})
```

#### Output:
```
100000000000000.01 ≅ 100000000000000.011: false
100.01 ≅ 100.011: false
1000000000.0000001 ≅ 1000000000.0000001: true
0.001 ≅ 0.0010000001: false
0.000000000000000000000101 ≅ 0: false
2 ≅ 2: true
-2 ≅ -2: true
-2 ≅ -2: true
3 ≅ 3: true
-3-7.82914889268316957969274243345625157631318402415e-58i ≅ -3: true
100000000000000003 ≅ 100000000000000004: false
3.14159265358979323846 ≅ 3.14159265358979324: false
```


The Number **n.round(-k)** can be used for rounding the number *n* to *k* decimal places. A positive argument can be used for rounding before the decimal point.

```ruby
var a = 100000000000000.01
var b = 100000000000000.011
 
# Rounding at 2 and 3 decimal places, respectively
say (round(a, -2) == round(b, -2))      # true
say (round(a, -3) == round(b, -3))      # false
```


There is also the built-in **approx\_cmp(a, b, k)** method, which is equivalent with **a.round(k) &lt;=&gt; b.round(k)**.

```ruby
var a = 22/7
var b = Num.pi
 
say ("22/7 ≅ π at 2 decimals: ", approx_cmp(a, b, -2) == 0)
say ("22/7 ≅ π at 3 decimals: ", approx_cmp(a, b, -3) == 0)
```

#### Output:
```
22/7 ≅ π at 2 decimals: true
22/7 ≅ π at 3 decimals: false
```


Additionally, the **rat\_approx** method can be used for computing a very good rational approximation to a given real value:

```ruby
say (1.33333333.rat_approx == 4/3)   # true
say (zeta(-5).rat_approx == -1/252)  # true
```


Rational approximations illustrated for substrings of PI:

```ruby
for k in (3..19) {
    var r = Str(Num.pi).first(k)
    say ("rat_approx(#{r}) = ", Num(r).rat_approx.as_frac)
}
```

#### Output:
```
rat_approx(3.1) = 31/10
rat_approx(3.14) = 22/7
rat_approx(3.141) = 245/78
rat_approx(3.1415) = 333/106
rat_approx(3.14159) = 355/113
rat_approx(3.141592) = 355/113
rat_approx(3.1415926) = 86953/27678
rat_approx(3.14159265) = 102928/32763
rat_approx(3.141592653) = 103993/33102
rat_approx(3.1415926535) = 1354394/431117
rat_approx(3.14159265358) = 833719/265381
rat_approx(3.141592653589) = 17925491/5705861
rat_approx(3.1415926535897) = 126312511/40206521
rat_approx(3.14159265358979) = 144029661/45846065
rat_approx(3.141592653589793) = 325994779/103767361
rat_approx(3.1415926535897932) = 903259831/287516534
rat_approx(3.14159265358979323) = 1726375805/549522486
```
