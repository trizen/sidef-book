[1]: https://rosettacode.org/wiki/Check_Machin-like_formulas

# [Check Machin-like formulas][1]

```ruby
var equationtext = <<'EOT'
  pi/4 = arctan(1/2) + arctan(1/3)
  pi/4 = 2*arctan(1/3) + arctan(1/7)
  pi/4 = 4*arctan(1/5) - arctan(1/239)
  pi/4 = 5*arctan(1/7) + 2*arctan(3/79)
  pi/4 = 5*arctan(29/278) + 7*arctan(3/79)
  pi/4 = arctan(1/2) + arctan(1/5) + arctan(1/8)
  pi/4 = 4*arctan(1/5) - arctan(1/70) + arctan(1/99)
  pi/4 = 5*arctan(1/7) + 4*arctan(1/53) + 2*arctan(1/4443)
  pi/4 = 6*arctan(1/8) + 2*arctan(1/57) + arctan(1/239)
  pi/4 = 8*arctan(1/10) - arctan(1/239) - 4*arctan(1/515)
  pi/4 = 12*arctan(1/18) + 8*arctan(1/57) - 5*arctan(1/239)
  pi/4 = 16*arctan(1/21) + 3*arctan(1/239) + 4*arctan(3/1042)
  pi/4 = 22*arctan(1/28) + 2*arctan(1/443) - 5*arctan(1/1393) - 10*arctan(1/11018)
  pi/4 = 22*arctan(1/38) + 17*arctan(7/601) + 10*arctan(7/8149)
  pi/4 = 44*arctan(1/57) + 7*arctan(1/239) - 12*arctan(1/682) + 24*arctan(1/12943)
  pi/4 = 88*arctan(1/172) + 51*arctan(1/239) + 32*arctan(1/682) + 44*arctan(1/5357) + 68*arctan(1/12943)
  pi/4 = 88*arctan(1/172) + 51*arctan(1/239) + 32*arctan(1/682) + 44*arctan(1/5357) + 68*arctan(1/12944)
EOT

func parse_eqn(equation) {
    static eqn_re = %r{
    (^ \s* pi/4 \s* = \s* )?                 # LHS of equation
    (?:                                      # RHS
        \s* ( [-+] )? \s*
        (?: ( \d+ ) \s* \*)?
        \s* arctan\((.*?)\)
    )}x

    gather {
        for lhs,sign,mult,rat in (equation.findall(eqn_re)) {
            take([
                [+1, -1][sign == '-'] * (mult ? Num(mult) : 1),
                Num(rat)
            ])
        }
    }
}

func tanEval(coef, f) {
    return f if (coef == 1)
    return -tanEval(-coef, f) if (coef < 0)
    var ca = coef>>1
    var cb = (coef - ca)
    var (a, b) = (tanEval(ca, f), tanEval(cb, f))
    (a + b) / (1 - a*b)
}

func tans(xs) {
    var xslen = xs.len
    return tanEval(xs[0]...) if (xslen == 1)
    var (aa, bb) = xs.part(xslen>>1)
    var (a, b) = (tans(aa), tans(bb))
    (a + b) / (1 - a*b)
}

var machins = equationtext.lines.map(parse_eqn)

for machin,eqn in (machins ~Z equationtext.lines) {
    var ans = tans(machin)
    printf("%5s: %s\n", (ans == 1 ? 'OK' : 'ERROR'), eqn)
}
```

#### Output:
```
   OK:   pi/4 = arctan(1/2) + arctan(1/3)
   OK:   pi/4 = 2*arctan(1/3) + arctan(1/7)
   OK:   pi/4 = 4*arctan(1/5) - arctan(1/239)
   OK:   pi/4 = 5*arctan(1/7) + 2*arctan(3/79)
   OK:   pi/4 = 5*arctan(29/278) + 7*arctan(3/79)
   OK:   pi/4 = arctan(1/2) + arctan(1/5) + arctan(1/8)
   OK:   pi/4 = 4*arctan(1/5) - arctan(1/70) + arctan(1/99)
   OK:   pi/4 = 5*arctan(1/7) + 4*arctan(1/53) + 2*arctan(1/4443)
   OK:   pi/4 = 6*arctan(1/8) + 2*arctan(1/57) + arctan(1/239)
   OK:   pi/4 = 8*arctan(1/10) - arctan(1/239) - 4*arctan(1/515)
   OK:   pi/4 = 12*arctan(1/18) + 8*arctan(1/57) - 5*arctan(1/239)
   OK:   pi/4 = 16*arctan(1/21) + 3*arctan(1/239) + 4*arctan(3/1042)
   OK:   pi/4 = 22*arctan(1/28) + 2*arctan(1/443) - 5*arctan(1/1393) - 10*arctan(1/11018)
   OK:   pi/4 = 22*arctan(1/38) + 17*arctan(7/601) + 10*arctan(7/8149)
   OK:   pi/4 = 44*arctan(1/57) + 7*arctan(1/239) - 12*arctan(1/682) + 24*arctan(1/12943)
   OK:   pi/4 = 88*arctan(1/172) + 51*arctan(1/239) + 32*arctan(1/682) + 44*arctan(1/5357) + 68*arctan(1/12943)
ERROR:   pi/4 = 88*arctan(1/172) + 51*arctan(1/239) + 32*arctan(1/682) + 44*arctan(1/5357) + 68*arctan(1/12944)
```
