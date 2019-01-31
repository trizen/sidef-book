[1]: https://rosettacode.org/wiki/Strong_and_weak_primes

# [Strong and weak primes][1]

```ruby
var primes = 10_000_019.primes
 
var (*strong, *weak, *balanced)
 
for k in (1 ..^ primes.end) {
    var p = primes[k]
 
    given((primes[k-1] + primes[k+1])/2) { |x|
        case (x > p) {     weak << p }
        case (x < p) {   strong << p }
        else         { balanced << p }
    }
}
 
for pr, type, d, c1, c2 in [
    [  strong, 'strong',   36, 1e6, 1e7],
    [    weak, 'weak',     37, 1e6, 1e7],
    [balanced, 'balanced', 28, 1e6, 1e7],
] {
    say ("\nFirst #{d} #{type} primes:\n", pr.first(d).map{.commify}.join(' '))
    say ("Count of #{type} primes <= #{c1.commify}:  ", pr.first_index { _ > 1e6 }.commify)
    say ("Count of #{type} primes <= #{c2.commify}: " , pr.len.commify)
}
```

#### Output:
```
First 36 strong primes:
11 17 29 37 41 59 67 71 79 97 101 107 127 137 149 163 179 191 197 223 227 239 251 269 277 281 307 311 331 347 367 379 397 419 431 439
Count of strong primes <= 1,000,000:  37,723
Count of strong primes <= 10,000,000: 320,991

First 37 weak primes:
3 7 13 19 23 31 43 47 61 73 83 89 103 109 113 131 139 151 167 181 193 199 229 233 241 271 283 293 313 317 337 349 353 359 383 389 401
Count of weak primes <= 1,000,000:  37,780
Count of weak primes <= 10,000,000: 321,750

First 28 balanced primes:
5 53 157 173 211 257 263 373 563 593 607 653 733 947 977 1,103 1,123 1,187 1,223 1,367 1,511 1,747 1,753 1,907 2,287 2,417 2,677 2,903
Count of balanced primes <= 1,000,000:  2,994
Count of balanced primes <= 10,000,000: 21,837
```