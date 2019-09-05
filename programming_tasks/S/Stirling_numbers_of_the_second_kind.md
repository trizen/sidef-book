[1]: https://rosettacode.org/wiki/Stirling_numbers_of_the_second_kind

# [Stirling numbers of the second kind][1]

```ruby
func S2(n, k) {     # Stirling numbers of the second kind
    stirling2(n, k)
}
 
const r = (0..12)
 
var triangle = r.map {|n| 0..n -> map {|k| S2(n, k) } }
var widths   = r.map {|n| r.map {|k| (triangle[k][n] \\ 0).len }.max }
 
say ('n\k ', r.map {|n| "%*s" % (widths[n], n) }.join(' '))
 
r.each {|n|
    var str = ('%-3s ' % n)
    str += triangle[n].map_kv {|k,v| "%*s" % (widths[k], v) }.join(' ')
    say str
}
 
with (100) {|n|
    say "\nMaximum value from the S2(#{n}, *) row:"
    say { S2(n, _) }.map(^n).max
}
```

#### Output:
```
n\k 0 1    2     3      4       5       6      7      8     9   10 11 12
0   1
1   0 1
2   0 1    1
3   0 1    3     1
4   0 1    7     6      1
5   0 1   15    25     10       1
6   0 1   31    90     65      15       1
7   0 1   63   301    350     140      21      1
8   0 1  127   966   1701    1050     266     28      1
9   0 1  255  3025   7770    6951    2646    462     36     1
10  0 1  511  9330  34105   42525   22827   5880    750    45    1
11  0 1 1023 28501 145750  246730  179487  63987  11880  1155   55  1
12  0 1 2047 86526 611501 1379400 1323652 627396 159027 22275 1705 66 1

Maximum value from the S2(100, *) row:
7769730053598745155212806612787584787397878128370115840974992570102386086289805848025074822404843545178960761551674
```


Alternatively, the **S2(n,k)** function can be defined as:

```ruby
func S2((0), (0)) { 1 }
func S2(_, (0))   { 0 }
func S2((0), _)   { 0 }
func S2(n, k) is cached { S2(n-1, k)*k + S2(n-1, k-1) }
```
