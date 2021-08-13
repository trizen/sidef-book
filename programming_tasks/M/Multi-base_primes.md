[1]: https://rosettacode.org/wiki/Multi-base_primes

# [Multi-base primes][1]

```ruby
func max_prime_bases(ndig, maxbase=36) {
 
    var maxprimebases = [[]]
    var nwithbases = [0]
    var maxprime = (10**ndig - 1)
 
    for p in (idiv(maxprime + 1, 10) .. maxprime) {
        var dig = p.digits
        var bases = (2..maxbase -> grep {|b| dig.all { _ < b } && dig.digits2num(b).is_prime })
        if (bases.len > maxprimebases.first.len) {
            maxprimebases = [bases]
            nwithbases = [p]
        }
        elsif (bases.len == maxprimebases.first.len) {
            maxprimebases << bases
            nwithbases << p
        }
    }
 
    var (alen, vlen) = (maxprimebases.first.len, maxprimebases.len)
 
    say("\nThe maximum number of prime valued bases for base 10 numeric strings of length ",
        ndig, " is #{alen}. The base 10 value list of ", vlen > 1 ? "these" : "this", " is:")
    maxprimebases.each_kv {|k,v| say(nwithbases[k], " => ", v) }
}
 
for n in (1..5) {
    max_prime_bases(n)
}
```

#### Output:
```
The maximum number of prime valued bases for base 10 numeric strings of length 1 is 34. The base 10 value list of this is:
2 => [3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24, 25, 26, 27, 28, 29, 30, 31, 32, 33, 34, 35, 36]

The maximum number of prime valued bases for base 10 numeric strings of length 2 is 18. The base 10 value list of this is:
21 => [3, 5, 6, 8, 9, 11, 14, 15, 18, 20, 21, 23, 26, 29, 30, 33, 35, 36]

The maximum number of prime valued bases for base 10 numeric strings of length 3 is 18. The base 10 value list of these is:
131 => [4, 5, 7, 8, 9, 10, 12, 14, 15, 18, 19, 20, 23, 25, 27, 29, 30, 34]
551 => [6, 7, 11, 13, 14, 15, 16, 17, 19, 21, 22, 24, 25, 26, 30, 32, 35, 36]
737 => [8, 9, 11, 12, 13, 15, 16, 17, 19, 22, 23, 24, 25, 26, 29, 30, 31, 36]

The maximum number of prime valued bases for base 10 numeric strings of length 4 is 19. The base 10 value list of these is:
1727 => [8, 9, 11, 12, 13, 15, 16, 17, 19, 20, 22, 23, 24, 26, 27, 29, 31, 33, 36]
5347 => [8, 9, 10, 11, 12, 13, 16, 18, 19, 22, 24, 25, 26, 30, 31, 32, 33, 34, 36]

The maximum number of prime valued bases for base 10 numeric strings of length 5 is 18. The base 10 value list of this is:
30271 => [8, 10, 12, 13, 16, 17, 18, 20, 21, 23, 24, 25, 31, 32, 33, 34, 35, 36]
```
