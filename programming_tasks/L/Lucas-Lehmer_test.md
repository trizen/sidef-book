[1]: http://rosettacode.org/wiki/Lucas-Lehmer_test

# [Lucas-Lehmer test][1]

```ruby
func is_mersenne_prime(p) {
    return true if (p == 2)
    var s = 4
    var M = (2**p - 1)
    { s = powmod(s, 2, M)-2 } * (p-2)
    s == 0
}

Inf.times {|n|
    if (n.is_prime && is_mersenne_prime(n)) {
        say "M#{n}"
    }
}
```

#### Output:
```
M2
M3
M5
M7
M13
M17
M19
M31
M61
M89
M107
M127
M521
M607
M1279
M2203
M2281
^C
```
