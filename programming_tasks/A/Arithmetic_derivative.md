[1]: https://rosettacode.org/wiki/Arithmetic_derivative

# [Arithmetic derivative][1]

Built-in as **Number#arithmetic\_derivative**:

```ruby
say "Arithmetic derivative for n in range [-99, 100]:"
-99 .. 100 -> map { .arithmetic_derivative }.each_slice(10, {|*a|
    a.map { '%4s' % _ }.join(' ').say
})

say "\nArithmetic derivative D(10^n)/7 for n in range [1, 20]:"
for n in (1..20) {
    say "D(10^#{n})/7 = #{arithmetic_derivative(10**n) / 7}"
}
```

#### Output:
```
Arithmetic derivative for n in range [-99, 100]:
 -75  -77   -1 -272  -24  -49  -34  -96  -20 -123
  -1 -140  -32  -45  -22 -124   -1  -43 -108 -176
  -1  -71  -18  -80  -55  -39   -1 -156   -1  -59
 -26  -72   -1  -61  -18 -192  -51  -33   -1  -92
  -1  -31  -22  -92  -16  -81   -1  -56  -20  -45
 -14 -112   -1  -25  -39  -48   -1  -41   -1  -68
 -16  -21   -1  -60  -12  -19  -14  -80   -1  -31
  -1  -32  -27  -15  -10  -44   -1  -13  -10  -24
  -1  -21   -1  -32   -8   -9   -1  -16   -1   -7
  -6  -12   -1   -5   -1   -4   -1   -1    0    0
   0    1    1    4    1    5    1   12    6    7
   1   16    1    9    8   32    1   21    1   24
  10   13    1   44   10   15   27   32    1   31
   1   80   14   19   12   60    1   21   16   68
   1   41    1   48   39   25    1  112   14   45
  20   56    1   81   16   92   22   31    1   92
   1   33   51  192   18   61    1   72   26   59
   1  156    1   39   55   80   18   71    1  176
 108   43    1  124   22   45   32  140    1  123
  20   96   34   49   24  272    1   77   75  140

Arithmetic derivative D(10^n)/7 for n in range [1, 20]:
D(10^1)/7 = 1
D(10^2)/7 = 20
D(10^3)/7 = 300
D(10^4)/7 = 4000
D(10^5)/7 = 50000
D(10^6)/7 = 600000
D(10^7)/7 = 7000000
D(10^8)/7 = 80000000
D(10^9)/7 = 900000000
D(10^10)/7 = 10000000000
D(10^11)/7 = 110000000000
D(10^12)/7 = 1200000000000
D(10^13)/7 = 13000000000000
D(10^14)/7 = 140000000000000
D(10^15)/7 = 1500000000000000
D(10^16)/7 = 16000000000000000
D(10^17)/7 = 170000000000000000
D(10^18)/7 = 1800000000000000000
D(10^19)/7 = 19000000000000000000
D(10^20)/7 = 200000000000000000000
```


Explicit implementation:

```ruby
subset Integer  < Number   { .is_int   }
subset Positive < Integer  { .is_pos   }
subset Negative < Integer  { .is_neg   }
subset Prime    < Positive { .is_prime }

func arithmetic_derivative((0)) { 0 }
func arithmetic_derivative((1)) { 0 }

func arithmetic_derivative(Prime _) { 1 }

func arithmetic_derivative(Negative n) {
    -arithmetic_derivative(-n)
}

func arithmetic_derivative(Positive n) is cached {

    var a = n.factor.rand
    var b = n/a

    arithmetic_derivative(a)*b + a*arithmetic_derivative(b)
}

func arithmetic_derivative(Number n) {
    var (a, b) = n.nude
    (arithmetic_derivative(a)*b - arithmetic_derivative(b)*a) / b**2
}
```
