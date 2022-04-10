[1]: https://rosettacode.org/wiki/Largest_difference_between_adjacent_primes

# [Largest difference between adjacent primes][1]

```ruby
func prime_gap_records(upto) {
 
    var gaps = []
    var p = 2
 
    each_prime(p.next_prime, upto, {|q|
        gaps[q-p] := p
        p = q
    })
 
    gaps.grep { defined(_) }
}
 
var upto   = 1e8
var primes = prime_gap_records(upto)
 
for n in (2 .. upto.ilog10) {
 
    var b = primes.last_by {|p| p < 10**n } \\ break
 
    printf("Largest prime gap up to 10^%s is %3s between %s and %s\n",
        n, b.next_prime - b, b, b.next_prime)
}
```

#### Output:
```
Largest prime gap up to 10^2 is   8 between 89 and 97
Largest prime gap up to 10^3 is  20 between 887 and 907
Largest prime gap up to 10^4 is  36 between 9551 and 9587
Largest prime gap up to 10^5 is  72 between 31397 and 31469
Largest prime gap up to 10^6 is 114 between 492113 and 492227
Largest prime gap up to 10^7 is 154 between 4652353 and 4652507
Largest prime gap up to 10^8 is 220 between 47326693 and 47326913
```
