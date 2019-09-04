[1]: https://rosettacode.org/wiki/Stirling_numbers_of_the_first_kind

# [Stirling numbers of the first kind][1]

```ruby
func S1(n, k) {     # unsigned Stirling numbers of the first kind
    stirling(n, k).abs
}
 
const r = (0..12)
 
var triangle = r.map {|n| 0..n -> map {|k| S1(n, k) } }
var widths   = r.map {|n| r.map {|k| (triangle[k][n] \\ 0).len }.max }
 
say ('n\k ', r.map {|n| "%*s" % (widths[n], n) }.join(' '))
 
r.each {|n|
    var str = ('%-3s ' % n)
    str += triangle[n].map_kv {|k,v| "%*s" % (widths[k], v) }.join(' ')
    say str
}
 
with (100) {|n|
    say "\nMaximum value from the S1(#{n}, *) row:"
    say { S1(n, _) }.map(^n).max
}
```

#### Output:
```
n\k 0        1         2         3         4        5        6       7      8     9   10 11 12
0   1
1   0        1
2   0        1         1
3   0        2         3         1
4   0        6        11         6         1
5   0       24        50        35        10        1
6   0      120       274       225        85       15        1
7   0      720      1764      1624       735      175       21       1
8   0     5040     13068     13132      6769     1960      322      28      1
9   0    40320    109584    118124     67284    22449     4536     546     36     1
10  0   362880   1026576   1172700    723680   269325    63273    9450    870    45    1
11  0  3628800  10628640  12753576   8409500  3416930   902055  157773  18150  1320   55  1
12  0 39916800 120543840 150917976 105258076 45995730 13339535 2637558 357423 32670 1925 66 1

Maximum value from the S1(100, *) row:
19710908747055261109287881673376044669240511161402863823515728791076863288440277983854056472903481625299174865860036734731122707870406148096000000000000000000
```


Alternatively, the **S1(n,k)** function can be defined as:

```ruby
func S1((0), (0)) { 1 }
func S1(_, (0))   { 0 }
func S1((0), _)   { 0 }
func S1(n, k) is cached { S1(n-1, k-1) + (n-1)*S1(n-1, k) }
```
