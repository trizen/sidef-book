[1]: https://rosettacode.org/wiki/Greatest_prime_dividing_the_n-th_cubefree_number

# [Greatest prime dividing the n-th cubefree number][1]

### Version 1



Built-in as **Number#nth\_cubefree()**:

```ruby
say "The first 100 terms of A370833 are:"
cubefree(100.nth_cubefree).map{.gpf}.each_slice(10, {|*a|
    a.map { '%3s' % _ }.join(' ').say
}); say ''

for n in (1..20) {
    say ("a(10^#{n}) = ", nth_cubefree(10**n).gpf)
}
```

#### Output:
```
The first 100 terms of A370833 are:
  1   2   3   2   5   3   7   3   5  11
  3  13   7   5  17   3  19   5   7  11
 23   5  13   7  29   5  31  11  17   7
  3  37  19  13  41   7  43  11   5  23
 47   7   5  17  13  53  11  19  29  59
  5  61  31   7  13  11  67  17  23   7
 71  73  37   5  19  11  13  79  41  83
  7  17  43  29  89   5  13  23  31  47
 19  97   7  11   5 101  17 103   7  53
107 109  11  37 113  19  23  29  13  59

a(10^1) = 11
a(10^2) = 59
a(10^3) = 109
a(10^4) = 101
a(10^5) = 1693
a(10^6) = 1202057
a(10^7) = 1202057
a(10^8) = 20743
a(10^9) = 215461
a(10^10) = 1322977
a(10^11) = 145823
a(10^12) = 400685634379
a(10^13) = 1498751
a(10^14) = 57349
a(10^15) = 74509198733
a(10^16) = 632661527978737
a(10^17) = 3018045307
a(10^18) = 89387
a(10^19) = 14563696231181
a(10^20) = 13237054323968663
```


### Version 2



Explicit implementation:

```ruby
func powerfree_count(n, k=2) {
    var sum = 0
    n.iroot(k).each_squarefree {|v|
        sum += (moebius(v) * idiv(n, v**k))
    }
    return sum
}

func nth_powerfree(n,k=2) {

    n <= 0 && return NaN
    n == 1 && return 1

    var v = int(zeta(k)*n)
    var c = powerfree_count(v, k)

    while (!v.is_powerfree(k)) {
        --v
    }

    while (c != n) {
        var j = (n <=> c)
        v += j
        c += j
        v += j while !v.is_powerfree(k)
    }

    return v
}

say {|n| nth_powerfree(n, 3).gpf }.map(1..100)

for n in (1..20) {
    say ("a(10^#{n}) = ", nth_powerfree(10**n, 3).gpf)
}
```


[Try it online!](https://tio.run/##ZZLRcoIwEEXf@YrVzjgJ1Qy0r@In@AO1dVIMYwQDDRDbAt9ON4AUNQ/MhJu9d/ckuTyIqG2jUoWQpRehIy3EPkxLVRC1hDh4oVA5gMtwDXl5hgC8bu8zppjUaVqQmMJqA4KHR6hqU3eyXfb4cwDknIpPWebEUHBBHqSx1sZ1Y0pBRmCYzPf5V8m1sOldedN9tShKrayP0zhO1yQeHftEm/janmIRD4tU78V3xniSYCdZVkOWvfnvsIYYHa8WqjjeevRD9jawxgFhsbhmb/l2EIIA/IngOyMWg1AkAvsVBUcYrqKjFKJ0z9UgV9pXX44yEUBmN1OZpQVTjRhXKzMwmdaEMAtATc/ZvBPmETvEBkL6r9hrOI3b8Hbbq4PvYyvT7GF2Y1nm/Achq/qBJ7zS4TJYwvMCdjsE17Azzwg@Gt/zcPgo1YhUKuh@jY/MepI5J7738VSphuI08@VdgO@57kMIxY7a9g8)
