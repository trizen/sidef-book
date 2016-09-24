[1]: http://rosettacode.org/wiki/Cipolla's_algorithm

# [Cipolla's algorithm][1]

```ruby
func cipolla(n, p) {
    func legendre_symbol(a) {
        expmod(a, (p-1)//2, p)
    }
 
    if (legendre_symbol(n) != 1) {
        return nil
    }
 
    var (a = 0, ω2 = 0)
    loop {
        ω2 = ((a*a - n) % p)
        if (legendre_symbol(ω2) == p-1) {
            break
        }
        ++a
    }
 
    struct point { x, y }
 
    func mul(a, b) {
        point((a.x*b.x + a.y*b.y*ω2) % p, (a.x*b.y + b.x*a.y) % p)
    }
 
    var r = point(1, 0)
    var s = point(a, 1)
 
    for (var n = ((p+1) >> 1); n > 0; n >>= 1) {
        r = mul(r, s) if n.is_odd
        s = mul(s, s)
    }
 
    r.y == 0 ? r.x : nil
}
 
var tests = [
    [10, 13],
    [56, 101],
    [8218, 10007],
    [8219, 10007],
    [331575, 1000003],
    [665165880, 1000000007],
    [881398088036 1000000000039],
    [34035243914635549601583369544560650254325084643201, 10**50 + 151],
]
 
for n,p in tests {
    var r = cipolla(n, p)
    if (defined(r)) {
        say "Roots of #{n} are (#{r} #{p-r}) mod #{p}"
    } else {
        say "No solution for (#{n}, #{p})"
    }
}
```

#### Output:
```
Roots of 10 are (6 7) mod 13
Roots of 56 are (37 64) mod 101
Roots of 8218 are (9872 135) mod 10007
No solution for (8219, 10007)
Roots of 331575 are (855842 144161) mod 1000003
Roots of 665165880 are (475131702 524868305) mod 1000000007
Roots of 881398088036 are (791399408049 208600591990) mod 1000000000039
Roots of 34035243914635549601583369544560650254325084643201 are (82563118828090362261378993957450213573687113690751 17436881171909637738621006042549786426312886309400) mod 100000000000000000000000000000000000000000000000151
```