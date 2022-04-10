[1]: https://rosettacode.org/wiki/Magic_constant

# [Magic constant][1]

```ruby
func f(n) {
    (n+2) * ((n+2)**2 + 1) / 2
}
 
func order(n) {
    iroot(2*n, 3) + 1
}
 
say ("First 20 terms: ", f.map(1..20).join(' '))
say ("1000th term: ", f(1000), " with order ", order(f(1000)))
 
for n in (1 .. 20) {
    printf("order(10^%-2s) = %s\n", n, order(10**n))
}
```

#### Output:
```
First 20 terms: 15 34 65 111 175 260 369 505 671 870 1105 1379 1695 2056 2465 2925 3439 4010 4641 5335
1000th term: 503006505 with order 1003
order(10^1 ) = 3
order(10^2 ) = 6
order(10^3 ) = 13
order(10^4 ) = 28
order(10^5 ) = 59
order(10^6 ) = 126
order(10^7 ) = 272
order(10^8 ) = 585
order(10^9 ) = 1260
order(10^10) = 2715
order(10^11) = 5849
order(10^12) = 12600
order(10^13) = 27145
order(10^14) = 58481
order(10^15) = 125993
order(10^16) = 271442
order(10^17) = 584804
order(10^18) = 1259922
order(10^19) = 2714418
order(10^20) = 5848036
```
