[1]: http://rosettacode.org/wiki/Tonelli-Shanks_algorithm

# [Tonelli-Shanks algorithm][1]

```ruby
func tonelli(n, p) {
    legendre(n, p) == 1 || die "not a square (mod p)"
    var q = p-1
    var s = valuation(q, 2)
    s == 1 ? return(powmod(n, (p + 1) >> 2, p)) : (q >>= s)
    var c = powmod(2 ..^ p -> first {|z| legendre(z, p) == -1}, q, p)
    var r = powmod(n, (q + 1) >> 1, p)
    var t = powmod(n, q, p)
    var m = s
    var t2 = 0
    while (!p.divides(t - 1)) {
        t2 = ((t * t) % p)
        var b
        for i in (1 ..^ m) {
            if (p.divides(t2 - 1)) {
                b = powmod(c, 1 << (m - i - 1), p)
                m = i
                break
            }
            t2 = ((t2 * t2) % p)
        }

        r = ((r * b) % p)
        c = ((b * b) % p)
        t = ((t * c) % p)
    }
    return r
}

var tests = [
    [10, 13], [56, 101], [1030, 10009], [44402, 100049],
    [665820697, 1000000009], [881398088036, 1000000000039],
    [41660815127637347468140745042827704103445750172002, 10**50 + 577],
]

for n,p in tests {
    var r = tonelli(n, p)
    assert((r*r - n) % p == 0)
    say "Roots of #{n} are (#{r}, #{p-r}) mod #{p}"
}
```

#### Output:
```
Roots of 10 are (7, 6) mod 13
Roots of 56 are (37, 64) mod 101
Roots of 1030 are (1632, 8377) mod 10009
Roots of 44402 are (30468, 69581) mod 100049
Roots of 665820697 are (378633312, 621366697) mod 1000000009
Roots of 881398088036 are (791399408049, 208600591990) mod 1000000000039
Roots of 41660815127637347468140745042827704103445750172002 are (32102985369940620849741983987300038903725266634508, 67897014630059379150258016012699961096274733366069) mod 100000000000000000000000000000000000000000000000577
```
