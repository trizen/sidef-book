[1]: http://rosettacode.org/wiki/Extensible_prime_generator

# [Extensible prime generator][1]

```ruby
say ("First 20: ", 20.nth_prime.primes.join(' '))
say ("Between 100 and 150: ", primes(100,150).join(' '))
say (prime_count(7700,8000), " primes between 7700 and 8000")
say ("10,000th prime: ", nth_prime(10_000))
```

#### Output:
```
First 20: 2 3 5 7 11 13 17 19 23 29 31 37 41 43 47 53 59 61 67 71
Between 100 and 150: 101 103 107 109 113 127 131 137 139 149
30 primes between 7700 and 8000
10,000th prime: 104729
```
