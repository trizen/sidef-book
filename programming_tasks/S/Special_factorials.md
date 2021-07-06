[1]: https://rosettacode.org/wiki/Special_factorials

# [Special factorials][1]

```ruby
func sf(n) { 1..n -> prod {|k| k! } }
func H(n)  { 1..n -> prod {|k| k**k } }
func af(n) { 1..n -> sum  {|k| (-1)**(n-k) * k! } }
func ef(n) { 1..n -> reduce({|a,b| b**a }, 1) }
 
func factorial_valuation(n,p) {
    (n - n.sumdigits(p)) / (p-1)
}
 
func p_adic_inverse (p, k) {
 
    var n = (k * (p - 1))
 
    while (factorial_valuation(n, p) < k) {
        n -= (n % p)
        n += p
    }
 
    return n
}
 
func rf(f) {
 
    return nil if (f < 0)
    return 0   if (f <= 1)
 
    var t = valuation(f, 2) || return nil
    var n = p_adic_inverse(2, t)
    var d = factor(n + 1)[-1]
 
    if (f.valuation(d) == factorial_valuation(n+1, d)) {
        ++n
    }
 
    for p in (primes(2, n)) {
        var v = factorial_valuation(n, p)
        f.valuation(p) == v || return nil
        f /= p**v
    }
 
    (f == 1) ? n : nil
}
 
say ('sf : ', 10.of(sf).join(' '))
say ('H  : ', 10.of(H).join(' '))
say ('af : ', 10.of(af).join(' '))
say ('ef : ', 5.of(ef).join(' '))
 
say "ef(5) has #{ef(5).len} digits"
 
say ('rf : ', [1, 2, 6, 24, 120, 720, 5040, 40320, 362880, 3628800].map(rf))
say ('rf(119) = ', rf(119) \\ 'nil')
say ('rf is defined for: ', 8.by { defined(rf(_)) }.join(', ' ) + ', ...')
```

#### Output:
```
sf : 1 1 2 12 288 34560 24883200 125411328000 5056584744960000 1834933472251084800000
H  : 1 1 4 108 27648 86400000 4031078400000 3319766398771200000 55696437941726556979200000 21577941222941856209168026828800000
af : 0 1 1 5 19 101 619 4421 35899 326981
ef : 1 1 2 9 262144
ef(5) has 183231 digits
rf : [0, 2, 3, 4, 5, 6, 7, 8, 9, 10]
rf(119) = nil
rf is defined for: 0, 1, 2, 6, 24, 120, 720, 5040, ...
```
