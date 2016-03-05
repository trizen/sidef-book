[1]: http://rosettacode.org/wiki/Extensible_prime_generator

# [Extensible prime generator][1]

```ruby
var nt = frequire('ntheory')
 
say ("First 20: ", nt.primes(nt.nth_prime(20)).join(' '))
say ("Between 100 and 150: ", nt.primes(100,150).join(' '))
say (nt.prime_count(7700,8000), " primes between 7700 and 8000")
say ("10,000th prime: ", nt.nth_prime(10_000))
```

#### Output:
```
First 20: 2 3 5 7 11 13 17 19 23 29 31 37 41 43 47 53 59 61 67 71
Between 100 and 150: 101 103 107 109 113 127 131 137 139 149
30 primes between 7700 and 8000
10,000th prime: 104729
```