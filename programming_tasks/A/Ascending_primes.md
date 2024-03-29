[1]: https://rosettacode.org/wiki/Ascending_primes

# [Ascending primes][1]

```ruby
func primes_with_ascending_digits(base = 10) {
 
    var list = []
    var digits = @(1..^base -> flip)
 
    var end_digits = digits.grep { .is_coprime(base) }
    list << digits.grep { .is_prime && !.is_coprime(base) }...
 
    for k in (0 .. digits.end) {
        digits.combinations(k, {|*a|
            var v = a.digits2num(base)
            end_digits.each {|d|
                var n = (v*base + d)
                next if ((n >= base) && (a[0] >= d))
                list << n if (n.is_prime)
            }
        })
    }
 
    list.sort
}
 
var arr = primes_with_ascending_digits()
 
say "There are #{arr.len} ascending primes.\n"
 
arr.each_slice(10, {|*a|
    say a.map { '%8s' % _ }.join(' ')
})
```

#### Output:
```
There are 100 ascending primes.

       2        3        5        7       13       17       19       23       29       37
      47       59       67       79       89      127      137      139      149      157
     167      179      239      257      269      347      349      359      367      379
     389      457      467      479      569     1237     1249     1259     1279     1289
    1367     1459     1489     1567     1579     1789     2347     2357     2389     2459
    2467     2579     2689     2789     3457     3467     3469     4567     4679     4789
    5689    12347    12379    12457    12479    12569    12589    12689    13457    13469
   13567    13679    13789    15679    23459    23567    23689    23789    25679    34589
   34679   123457   123479   124567   124679   125789   134789   145679   234589   235679
  235789   245789   345679   345689  1234789  1235789  1245689  1456789 12356789 23456789
```
