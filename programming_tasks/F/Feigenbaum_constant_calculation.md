[1]: https://rosettacode.org/wiki/Feigenbaum_constant_calculation

# [Feigenbaum constant calculation][1]

```ruby
var a1 = 1
var a2 = 0
var δ  = 3.2.float
 
say " i\tδ"
 
for i in (2..15) {
    var a0 = ((a1 - a2)/δ + a1)
    10.times {
        var (x, y) = (0, 0)
        2**i -> times {
            y = (1 - 2*x*y)
            x = (a0 - x²)
        }
        a0 -= x/y
    }
    δ = ((a1 - a2) / (a0 - a1))
    (a2, a1) = (a1, a0)
    printf("%2d %.8f\n", i, δ)
}
```

#### Output:
```
 i      δ
 2 3.21851142
 3 4.38567760
 4 4.60094928
 5 4.65513050
 6 4.66611195
 7 4.66854858
 8 4.66906066
 9 4.66917156
10 4.66919516
11 4.66920023
12 4.66920131
13 4.66920155
14 4.66920160
15 4.66920161
```