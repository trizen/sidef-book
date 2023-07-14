[1]: https://rosettacode.org/wiki/Extreme_floating_point_values

# [Extreme floating point values][1]

*NaN* and *Inf* literals can be used to represent the *Not-a-Number* and *Infinity* values, which are returned in special cases, such as *0/0* and *1/0*. However, one thing to notice, is that in Sidef there is no distinction between *0.0* and *-0.0* and can't be differentiated from each other.

```ruby
var inf = 1/0    # same as: Inf
var nan = 0/0    # same as: NaN

var exprs = [
  "1.0 / 0.0", "-1.0 / 0.0", "0.0 / 0.0", "- 0.0",
  "inf + 1", "5 - inf", "inf * 5", "inf / 5", "inf * 0",
  "1.0 / inf", "-1.0 / inf", "inf + inf", "inf - inf",
  "inf * inf", "inf / inf", "inf * 0.0", " 0 < inf", "inf == inf",
  "nan + 1", "nan * 5", "nan - nan", "nan * inf", "- nan",
  "nan == nan", "nan > 0", "nan < 0", "nan == 0", "0.0 == -0.0",
]

exprs.each { |expr|
  "%15s => %s\n".printf(expr, eval(expr))
}

say "-"*40
say("NaN equality: ",        NaN ==  nan)
say("Infinity equality: ",   Inf ==  inf)
say("-Infinity equality: ", -Inf == -inf)

say "-"*40
say("sqrt(-1)   = ",   sqrt(-1))
say("tanh(-Inf) = ", tanh(-inf))
say("(-Inf)**2  = ",  (-inf)**2)
say("(-Inf)**3  = ",  (-inf)**3)
say("acos(Inf)  = ",  acos(inf))
say("atan(Inf)  = ",  atan(inf))
say("log(-1)    = ",    log(-1))
say("atanh(Inf) = ", atanh(inf))
```

#### Output:
```
      1.0 / 0.0 => Inf
     -1.0 / 0.0 => -Inf
      0.0 / 0.0 => NaN
          - 0.0 => 0
        inf + 1 => Inf
        5 - inf => -Inf
        inf * 5 => Inf
        inf / 5 => Inf
        inf * 0 => NaN
      1.0 / inf => 0
     -1.0 / inf => 0
      inf + inf => Inf
      inf - inf => NaN
      inf * inf => Inf
      inf / inf => NaN
      inf * 0.0 => NaN
        0 < inf => true
     inf == inf => true
        nan + 1 => NaN
        nan * 5 => NaN
      nan - nan => NaN
      nan * inf => NaN
          - nan => NaN
     nan == nan => false
        nan > 0 =>
        nan < 0 =>
       nan == 0 => false
    0.0 == -0.0 => true
----------------------------------------
NaN equality: false
Infinity equality: true
-Infinity equality: true
----------------------------------------
sqrt(-1)   = i
tanh(-Inf) = -1
(-Inf)**2  = Inf
(-Inf)**3  = -Inf
acos(Inf)  = -Infi
atan(Inf)  = 1.57079632679489661923132169163975144209858469969
log(-1)    = 3.14159265358979323846264338327950288419716939938i
atanh(Inf) = 1.57079632679489661923132169163975144209858469969i
```
