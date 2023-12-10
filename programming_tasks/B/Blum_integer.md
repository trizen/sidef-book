[1]: https://rosettacode.org/wiki/Blum_integer

# [Blum integer][1]

Takes about 30 seconds:

```ruby
func blum_integers(upto) {

    var L = []
    var P = idiv(upto, 3).primes.grep{ .is_congruent(3, 4) }

    for i in (1..P.end) {
        var p = P[i]
        for j in (^i) {
            var t = p*P[j]
            break if (t > upto)
            L << t
        }
    }

    L.sort
}

func blum_first(n) {
    var upto = int(4.5*n*log(n) / log(log(n)))
    loop {
        var B = blum_integers(upto)
        if (B.len >= n) {
            return B.first(n)
        }
        upto *= 2
    }
}

with (50) {|n|
    say "The first #{n} Blum integers:"
    blum_first(n).slices(10).each { .map{ "%4s" % _ }.join.say }
}

say ''

for n in (26828, 1e5, 2e5, 3e5, 4e5) {
    var B = blum_first(n)
    say "#{n.commify}th Blum integer: #{B.last}"

    if (n == 4e5) {
        say ''
        for k in (1,3,7,9) {
            var T = B.grep { .is_congruent(k, 10) }
            say "#{k}: #{'%6s' % T.len} (#{T.len / B.len * 100}%)"
        }
    }
}
```

#### Output:
```
The first 50 Blum integers:
  21  33  57  69  77  93 129 133 141 161
 177 201 209 213 217 237 249 253 301 309
 321 329 341 381 393 413 417 437 453 469
 473 489 497 501 517 537 553 573 581 589
 597 633 649 669 681 713 717 721 737 749

26,828th Blum integer: 524273
100,000th Blum integer: 2075217
200,000th Blum integer: 4275533
300,000th Blum integer: 6521629
400,000th Blum integer: 8802377

1: 100005 (25.00125%)
3: 100067 (25.01675%)
7:  99989 (24.99725%)
9:  99939 (24.98475%)
```
