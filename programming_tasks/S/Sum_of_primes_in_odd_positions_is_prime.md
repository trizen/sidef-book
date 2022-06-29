[1]: https://rosettacode.org/wiki/Sum_of_primes_in_odd_positions_is_prime

# [Sum of primes in odd positions is prime][1]

```ruby
var sum = 0
1e3.primes.each_kv {|k,v|
    if (k+1 -> is_odd) {
        sum += v
        say "#{k+1} #{v} #{sum}" if sum.is_prime
    }
}
```

#### Output:
```
1 2 2
3 5 7
11 31 89
27 103 659
35 149 1181
67 331 5021
91 467 9923
95 499 10909
99 523 11941
119 653 17959
143 823 26879
```
