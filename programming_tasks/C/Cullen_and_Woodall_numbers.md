[1]: https://rosettacode.org/wiki/Cullen_and_Woodall_numbers

# [Cullen and Woodall numbers][1]

```ruby
func cullen(n)  { n * (1 << n) + 1 }
func woodall(n) { n * (1 << n) - 1 }
 
say "First 20 Cullen numbers:"
say cullen.map(1..20).join(' ')
 
say "\nFirst 20 Woodall numbers:"
say woodall.map(1..20).join(' ')
 
say "\nFirst 5 Cullen primes: (in terms of n)"
say 5.by { cullen(_).is_prime }.join(' ')
 
say "\nFirst 12 Woodall primes: (in terms of n)"
say 12.by { woodall(_).is_prime }.join(' ')
```

#### Output:
```
First 20 Cullen numbers:
3 9 25 65 161 385 897 2049 4609 10241 22529 49153 106497 229377 491521 1048577 2228225 4718593 9961473 20971521

First 20 Woodall numbers:
1 7 23 63 159 383 895 2047 4607 10239 22527 49151 106495 229375 491519 1048575 2228223 4718591 9961471 20971519

First 5 Cullen primes: (in terms of n)
1 141 4713 5795 6611

First 12 Woodall primes: (in terms of n)
2 3 6 30 75 81 115 123 249 362 384 462
```
