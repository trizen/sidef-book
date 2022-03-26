[1]: https://rosettacode.org/wiki/Prime_numbers_p_for_which_the_sum_of_primes_less_than_or_equal_to_p_is_prime

# [Prime numbers p for which the sum of primes less than or equal to p is prime][1]

```ruby
func primes_with_prime_sum(n, callback) {
    var s = 0
    n.each_prime {|p|
        s += p
        callback(p, s) if s.is_prime
    }
}
 
primes_with_prime_sum(1000, {|p,s|
    say "prime: #{'%3s' % p}   prime sum: #{'%5s' % s}"
})
```

#### Output:
```
prime:   2   prime sum:     2
prime:   3   prime sum:     5
prime:   7   prime sum:    17
prime:  13   prime sum:    41
prime:  37   prime sum:   197
prime:  43   prime sum:   281
prime: 281   prime sum:  7699
prime: 311   prime sum:  8893
prime: 503   prime sum: 22039
prime: 541   prime sum: 24133
prime: 557   prime sum: 25237
prime: 593   prime sum: 28697
prime: 619   prime sum: 32353
prime: 673   prime sum: 37561
prime: 683   prime sum: 38921
prime: 733   prime sum: 43201
prime: 743   prime sum: 44683
prime: 839   prime sum: 55837
prime: 881   prime sum: 61027
prime: 929   prime sum: 66463
prime: 953   prime sum: 70241
```
