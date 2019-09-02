[1]: https://rosettacode.org/wiki/N-smooth_numbers

# [N-smooth numbers][1]

```ruby
func smooth_generator(primes) {
    var s = primes.len.of { [1] }
    {
        var n = s.map { .first }.min
        { |i|
            s[i].shift if (s[i][0] == n)
            s[i] << (n * primes[i])
        } * primes.len
        n
    }
}
 
for p in (primes(2,29)) {
    var g = smooth_generator(p.primes)
    say ("First 25 #{'%2d'%p}-smooth numbers: ", 25.of { g.run }.join(' '))
}
 
say ''
 
for p in (primes(3,29)) {
    var g = smooth_generator(p.primes)
    say ("3,000th through 3,002nd #{'%2d'%p}-smooth numbers: ", 3002.of { g.run }.last(3).join(' '))
}
```

#### Output:
```
First 25  2-smooth numbers: 1 2 4 8 16 32 64 128 256 512 1024 2048 4096 8192 16384 32768 65536 131072 262144 524288 1048576 2097152 4194304 8388608 16777216
First 25  3-smooth numbers: 1 2 3 4 6 8 9 12 16 18 24 27 32 36 48 54 64 72 81 96 108 128 144 162 192
First 25  5-smooth numbers: 1 2 3 4 5 6 8 9 10 12 15 16 18 20 24 25 27 30 32 36 40 45 48 50 54
First 25  7-smooth numbers: 1 2 3 4 5 6 7 8 9 10 12 14 15 16 18 20 21 24 25 27 28 30 32 35 36
First 25 11-smooth numbers: 1 2 3 4 5 6 7 8 9 10 11 12 14 15 16 18 20 21 22 24 25 27 28 30 32
First 25 13-smooth numbers: 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 18 20 21 22 24 25 26 27 28
First 25 17-smooth numbers: 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 20 21 22 24 25 26 27
First 25 19-smooth numbers: 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 24 25 26
First 25 23-smooth numbers: 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25
First 25 29-smooth numbers: 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25

3,000th through 3,002nd  3-smooth numbers: 91580367978306252441724649472 92829823186414819915547541504 94096325042746502515294076928
3,000th through 3,002nd  5-smooth numbers: 278942752080 279936000000 281250000000
3,000th through 3,002nd  7-smooth numbers: 50176000 50331648 50388480
3,000th through 3,002nd 11-smooth numbers: 2112880 2116800 2117016
3,000th through 3,002nd 13-smooth numbers: 390000 390390 390625
3,000th through 3,002nd 17-smooth numbers: 145800 145860 146016
3,000th through 3,002nd 19-smooth numbers: 74256 74358 74360
3,000th through 3,002nd 23-smooth numbers: 46552 46575 46585
3,000th through 3,002nd 29-smooth numbers: 33516 33524 33534
```


Optionally, an efficient algorithm for checking if a given arbitrary large number is smooth over a given product of primes:

```ruby
func is_smooth_over_prod(n, k) {
 
    return true  if (n == 1)
    return false if (n <= 0)
 
    for (var g = gcd(n,k); g > 1; g = gcd(n,k)) {
        n /= g**valuation(n,g)        # remove any divisibility by g
        return true if (n == 1)       # smooth if n == 1
    }
 
    return false
}
 
for p in (503, 509, 521) {
    var k = p.primorial
    var a = {|n| is_smooth_over_prod(n, k) }.first(30_019).last(20)
    say ("30,000th through 30,019th #{p}-smooth numbers: ", a.join(' '))
}
```

#### Output:
```
30,000th through 30,019th 503-smooth numbers: 62913 62914 62916 62918 62920 62923 62926 62928 62930 62933 62935 62937 62944 62946 62951 62952 62953 62957 62959 62964
30,000th through 30,019th 509-smooth numbers: 62601 62602 62604 62607 62608 62609 62611 62618 62620 62622 62624 62625 62626 62628 62629 62634 62640 62643 62645 62646
30,000th through 30,019th 521-smooth numbers: 62287 62288 62291 62292 62300 62304 62307 62308 62310 62315 62320 62321 62322 62325 62328 62329 62330 62331 62335 62336
```
