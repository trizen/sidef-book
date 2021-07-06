[1]: https://rosettacode.org/wiki/Summarize_primes

# [Summarize primes][1]

```ruby
1000.primes.map_reduce {|a,b| a + b }.map_kv {|k,v|
    [k+1, prime(k+1), v]
}.grep { .tail.is_prime }.prepend(
    ['count', 'prime', 'sum']
).each_2d {|n,p,s|
    printf("%5s %6s %8s\n", n, p, s)
}
```

#### Output:
```
count  prime      sum
    1      2        2
    2      3        5
    4      7       17
    6     13       41
   12     37      197
   14     43      281
   60    281     7699
   64    311     8893
   96    503    22039
  100    541    24133
  102    557    25237
  108    593    28697
  114    619    32353
  122    673    37561
  124    683    38921
  130    733    43201
  132    743    44683
  146    839    55837
  152    881    61027
  158    929    66463
  162    953    70241
```
