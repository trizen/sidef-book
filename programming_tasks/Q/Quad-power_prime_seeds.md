[1]: https://rosettacode.org/wiki/Quad-power_prime_seeds

# [Quad-power prime seeds][1]

```ruby
var qpps = (1..Inf -> by(2).lazy.grep { .is_prime }.map {|n| (n-1)>>1 }.grep {|n|
    is_prime(n**2 + n + 1) && all_prime(n**3 + n + 1, n**4 + n + 1)
})

with (50) {|n|
    say "First #{n} quad-power prime seeds:"
    qpps.first(n).each_slice(10, {|*s| say s.map{ '%6s' % _ }.join(' ') })
}
```

#### Output:
```
First 50 quad-power prime seeds:
     1      2      5      6     69    131    426   1665   2129   2696
  5250   7929   9689  13545  14154  14286  16434  19760  25739  27809
 29631  36821  41819  46619  48321  59030  60500  61955  62321  73610
 77685  79646  80535  82655  85251  86996  91014  96566  97739 105939
108240 108681 119754 122436 123164 126489 140636 150480 153179 163070
```
