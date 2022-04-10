[1]: https://rosettacode.org/wiki/Earliest_difference_between_prime_gaps

# [Earliest difference between prime gaps][1]

```ruby
func prime_gap_records(upto) {
 
    var gaps = []
    var p = 3
 
    each_prime(p.next_prime, upto, {|q|
        gaps[q-p] := p
        p = q
    })
 
    gaps.grep { defined(_) }
}
 
var gaps = prime_gap_records(1e8)
 
for m in (1 .. gaps.max.len) {
    gaps.each_cons(2, {|p,q|
        if (abs(q-p) > 10**m) {
            say "10^#{m} -> (#{p}, #{q}) with gaps (#{
            p.next_prime-p}, #{q.next_prime-q}) and difference #{abs(q-p)}"
            break
        }
    })
}
```

#### Output:
```
10^1 -> (7, 23) with gaps (4, 6) and difference 16
10^2 -> (113, 1831) with gaps (14, 16) and difference 1718
10^3 -> (113, 1831) with gaps (14, 16) and difference 1718
10^4 -> (9551, 30593) with gaps (36, 38) and difference 21042
10^5 -> (173359, 31397) with gaps (70, 72) and difference 141962
10^6 -> (396733, 1444309) with gaps (100, 102) and difference 1047576
10^7 -> (2010733, 13626257) with gaps (148, 150) and difference 11615524
```
