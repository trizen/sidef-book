[1]: https://rosettacode.org/wiki/Minimum_multiple_of_m_where_digital_sum_equals_m

# [Minimum multiple of m where digital sum equals m][1]

```ruby
var e = Enumerator({|f|
    for n in (1..Inf) {
 
        var k = 0
        while (k.sumdigits != n) {
            k += n
        }
 
        f(k/n)
    }
})
 
var N = 60
var A = []
 
e.each {|v|
    A << v
    say A.splice.map { '%7s' % _ }.join(' ') if (A.len == 10)
    break if (--N <= 0)
}
```

#### Output:
```
      1       1       1       1       1       1       1       1       1      19
     19       4      19      19      13      28      28      11      46     199
     19     109      73      37     199      73      37     271     172    1333
    289     559    1303     847    1657     833    1027    1576    1282   17497
   4339    2119    2323   10909   11111   12826   14617   14581   16102  199999
  17449   38269   56413   37037 1108909  142498  103507  154981  150661 1333333
```
