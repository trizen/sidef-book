[1]: https://rosettacode.org/wiki/Apéry%27s_constant

# [Apéry&#039;s constant][1]

```ruby
local Num!PREC = 4*101
say "Actual value to 100 decimal places:\n#{zeta(3)}"

say "\nFirst 1000 terms of ζ(3) truncated to 100 decimal places. (accurate to 6 decimal places):";
say sum(1..1000, {|k| 1/k**3 }).as_float(101)

say "\nFirst 158 terms of Markov / Apéry representation truncated to 100 decimal places:";
say ((5/2)*sum(1..158, {|k|
    (-1)**(k-1) * (k!**2 / ((2*k)! * k**3))
}) -> as_float(101))

say "\nFirst 20 terms of Wedeniwski representation truncated to 100 decimal places:";
say ((1/24)*sum(^20, {|k|
    (-1)**k * (2*k + 1)!**3 * (2*k)!**3 * k!**3 * (
        126392*k**5 + 412708*k**4 + 531578*k**3 + 336367*k**2 + 104000*k + 12463
    ) / ((3*k + 2)! * (4*k + 3)!**3)
}) -> as_float(101))
```

#### Output:
```
Actual value to 100 decimal places:
1.2020569031595942853997381615114499907649862923404988817922715553418382057863130901864558736093352581

First 1000 terms of ζ(3) truncated to 100 decimal places. (accurate to 6 decimal places):
1.2020564036593442854830714115115999903483212709031775135036540966118572571921400836130084123260473112

First 158 terms of Markov / Apéry representation truncated to 100 decimal places:
1.2020569031595942853997381615114499907649862923404988817922715553418382057863130901864558736093352581

First 20 terms of Wedeniwski representation truncated to 100 decimal places:
1.2020569031595942853997381615114499907649862923404988817922715553418382057863130901864558736093352581
```
