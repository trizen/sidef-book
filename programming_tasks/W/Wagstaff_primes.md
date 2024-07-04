[1]: https://rosettacode.org/wiki/Wagstaff_primes

# [Wagstaff primes][1]

```ruby
var iter = Enumerator({|callback|
    var p = 2
    loop {
        var t = ((2**p + 1)/3)
        callback([p, t]) if t.is_prime
        p.next_prime!
    }
})

var n = 1
say "Index    Exponent         Prime"
say "-"*31

iter.each {|k|
    var (e, p) = k...
    p = "(#{p.len} digits)" if (n > 10)
    say "#{'%5s'%n} #{'%8s'%e} #{'%16s'%p}"
    break if (n == 24)
    ++n
}
```

#### Output:
```
Index    Exponent         Prime
-------------------------------
    1        3                3
    2        5               11
    3        7               43
    4       11              683
    5       13             2731
    6       17            43691
    7       19           174763
    8       23          2796203
    9       31        715827883
   10       43    2932031007403
   11       61      (18 digits)
   12       79      (24 digits)
   13      101      (30 digits)
   14      127      (38 digits)
   15      167      (50 digits)
   16      191      (58 digits)
   17      199      (60 digits)
   18      313      (94 digits)
   19      347     (104 digits)
   20      701     (211 digits)
   21     1709     (514 digits)
   22     2617     (788 digits)
   23     3539    (1065 digits)
   24     5807    (1748 digits)
```
