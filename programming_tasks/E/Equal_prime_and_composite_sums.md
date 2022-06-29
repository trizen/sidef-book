[1]: https://rosettacode.org/wiki/Equal_prime_and_composite_sums

# [Equal prime and composite sums][1]

```ruby
func f(n) {
 
    var (
        p = 2, sp = p,
        c = 4, sc = c,
    )
 
    var res = []
 
    while (res.len < n) {
        if (sc == sp) {
            res << [sp, c.composite_count, p.prime_count]
            sc += c.next_composite!
        }
        while (sp < sc) {
            sp += p.next_prime!
        }
        while (sc < sp) {
            sc += c.next_composite!
        }
    }
 
    return res
}
 
f(8).each_2d {|n, ci, pi|
    printf("%12s = %-9s = %s\n", n, "P(#{pi})", "C(#{ci})")
}
```

#### Output:
```
          10 = P(3)      = C(2)
        1988 = P(33)     = C(51)
       14697 = P(80)     = C(147)
       83292 = P(175)    = C(361)
     1503397 = P(660)    = C(1582)
    18859052 = P(2143)   = C(5699)
    93952013 = P(4556)   = C(12821)
 89171409882 = P(118785) = C(403341)
```


(takes ~6 seconds)
