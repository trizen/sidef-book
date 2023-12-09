[1]: https://rosettacode.org/wiki/Isqrt_(integer_square_root)_of_X

# [Isqrt (integer square root) of X][1]

Built-in:

```ruby
var n = 1234
say n.isqrt
say n.iroot(2)
```


Explicit implementation for the integer k-th root of n:

```ruby
func rootint(n, k=2) {
    return 0 if (n == 0)
    var (s, v) = (n, k - 1)
    loop {
        var u = ((v*s + (n // s**v)) // k)
        break if (u >= s)
        s = u
    }
    s
}
```


Implementation of integer square root of n (using the quadratic residue algorithm):

```ruby
func isqrt(x) { var (q, r) = (1, 0); while (q <= x) { q <<= 2 }
    while (q > 1) { q >>= 2; var t = x-r+q; r >>= 1
        if (t >= 0) { (x, r) = (t, r+q) } } r }

say isqrt.map(0..65).join(' '); printf("\n")

for n in (1..73 `by` 2) {
    printf("isqrt(7^%-2d): %42s\n", n, isqrt(7**n).commify) }
```

#### Output:
```
0 1 1 1 2 2 2 2 2 3 3 3 3 3 3 3 4 4 4 4 4 4 4 4 4 5 5 5 5 5 5 5 5 5 5 5 6 6 6 6 6 6 6 6 6 6 6 6 6 7 7 7 7 7 7 7 7 7 7 7 7 7 7 7 8 8

isqrt(7^1 ):                                          2
isqrt(7^3 ):                                         18
isqrt(7^5 ):                                        129
isqrt(7^7 ):                                        907
isqrt(7^9 ):                                      6,352
isqrt(7^11):                                     44,467
isqrt(7^13):                                    311,269
isqrt(7^15):                                  2,178,889
isqrt(7^17):                                 15,252,229
isqrt(7^19):                                106,765,608
isqrt(7^21):                                747,359,260
isqrt(7^23):                              5,231,514,822
isqrt(7^25):                             36,620,603,758
isqrt(7^27):                            256,344,226,312
isqrt(7^29):                          1,794,409,584,184
isqrt(7^31):                         12,560,867,089,291
isqrt(7^33):                         87,926,069,625,040
isqrt(7^35):                        615,482,487,375,282
isqrt(7^37):                      4,308,377,411,626,977
isqrt(7^39):                     30,158,641,881,388,842
isqrt(7^41):                    211,110,493,169,721,897
isqrt(7^43):                  1,477,773,452,188,053,281
isqrt(7^45):                 10,344,414,165,316,372,973
isqrt(7^47):                 72,410,899,157,214,610,812
isqrt(7^49):                506,876,294,100,502,275,687
isqrt(7^51):              3,548,134,058,703,515,929,815
isqrt(7^53):             24,836,938,410,924,611,508,707
isqrt(7^55):            173,858,568,876,472,280,560,953
isqrt(7^57):          1,217,009,982,135,305,963,926,677
isqrt(7^59):          8,519,069,874,947,141,747,486,745
isqrt(7^61):         59,633,489,124,629,992,232,407,216
isqrt(7^63):        417,434,423,872,409,945,626,850,517
isqrt(7^65):      2,922,040,967,106,869,619,387,953,625
isqrt(7^67):     20,454,286,769,748,087,335,715,675,381
isqrt(7^69):    143,180,007,388,236,611,350,009,727,669
isqrt(7^71):  1,002,260,051,717,656,279,450,068,093,686
isqrt(7^73):  7,015,820,362,023,593,956,150,476,655,802
```
