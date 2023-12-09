[1]: https://rosettacode.org/wiki/Extreme_primes

# [Extreme primes][1]

```ruby
var(c,p,n) = (0,0,0)

while (c < 50_000) {
    p.next_prime!
    n += p
    if (n.is_prime) {
        ++c
        if (c <= 30) {
            say "Sum of prime series up to #{p}: prime #{n}"
        }
        elsif (c ~~ [1000, 2000, 3000, 4000, 5000, 30_000, 40_000, 50_000]) {
            say ("Sum of #{c.commify} in prime series up to #{p}: prime #{n}")
        }
    }
}
```

#### Output:
```
Sum of prime series up to 2: prime 2
Sum of prime series up to 3: prime 5
Sum of prime series up to 7: prime 17
Sum of prime series up to 13: prime 41
Sum of prime series up to 37: prime 197
Sum of prime series up to 43: prime 281
Sum of prime series up to 281: prime 7699
Sum of prime series up to 311: prime 8893
Sum of prime series up to 503: prime 22039
Sum of prime series up to 541: prime 24133
Sum of prime series up to 557: prime 25237
Sum of prime series up to 593: prime 28697
Sum of prime series up to 619: prime 32353
Sum of prime series up to 673: prime 37561
Sum of prime series up to 683: prime 38921
Sum of prime series up to 733: prime 43201
Sum of prime series up to 743: prime 44683
Sum of prime series up to 839: prime 55837
Sum of prime series up to 881: prime 61027
Sum of prime series up to 929: prime 66463
Sum of prime series up to 953: prime 70241
Sum of prime series up to 1061: prime 86453
Sum of prime series up to 1163: prime 102001
Sum of prime series up to 1213: prime 109147
Sum of prime series up to 1249: prime 116533
Sum of prime series up to 1277: prime 119069
Sum of prime series up to 1283: prime 121631
Sum of prime series up to 1307: prime 129419
Sum of prime series up to 1321: prime 132059
Sum of prime series up to 1949: prime 263171
Sum of 1,000 in prime series up to 196831: prime 1657620079
Sum of 2,000 in prime series up to 495571: prime 9744982591
Sum of 3,000 in prime series up to 808837: prime 24984473177
Sum of 4,000 in prime series up to 1152763: prime 49394034691
Sum of 5,000 in prime series up to 1500973: prime 82195983953
Sum of 30,000 in prime series up to 12437401: prime 4889328757567
Sum of 40,000 in prime series up to 17245391: prime 9207632380589
Sum of 50,000 in prime series up to 22272277: prime 15118097491121
```
