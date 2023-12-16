[1]: https://rosettacode.org/wiki/Radical_of_an_integer

# [Radical of an integer][1]

Takes less than one second to run:

```ruby
with (50) {|n|
    say "Radicals of the first #{n} positive integers:"
    1..n -> map { .rad }.each_slice(10, {|*s|
        say s.map { '%2s' % _ }.join(' ')
    })
}

say ''; [99999, 499999, 999999].map {|n|
    say "rad(#{n}) = #{rad(n)}"
}

for limit in (1e6, 1e7, 1e8, 1e9) {
    say "\nCounting of k-omega primes <= #{limit.commify}:"
    for k in (1..Inf) {
        break if (pn_primorial(k) > limit)
        var c = k.omega_prime_count(limit)
        say "#{k}: #{c}"
        assert_eq(c, limit.prime_power_count) if (k == 1)
    }
}
```

#### Output:
```
Radicals of the first 50 positive integers:
 1  2  3  2  5  6  7  2  3 10
11  6 13 14 15  2 17  6 19 10
21 22 23  6  5 26  3 14 29 30
31  2 33 34 35  6 37 38 39 10
41 42 43 22 15 46 47  6  7 10

rad(99999) = 33333
rad(499999) = 3937
rad(999999) = 111111

Counting of k-omega primes <= 1,000,000:
1: 78734
2: 288726
3: 379720
4: 208034
5: 42492
6: 2285
7: 8

Counting of k-omega primes <= 10,000,000:
1: 665134
2: 2536838
3: 3642766
4: 2389433
5: 691209
6: 72902
7: 1716
8: 1

Counting of k-omega primes <= 100,000,000:
1: 5762859
2: 22724609
3: 34800362
4: 25789580
5: 9351293
6: 1490458
7: 80119
8: 719

Counting of k-omega primes <= 1,000,000,000:
1: 50851223
2: 206415108
3: 332590117
4: 269536378
5: 114407511
6: 24020091
7: 2124141
8: 55292
9: 138
```
