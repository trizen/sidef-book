[1]: https://rosettacode.org/wiki/Long_primes

# [Long primes][1]

The smallest divisor d of p-1 such that 10^d = 1 (mod p), is the length of the period of the decimal expansion of 1/p.

```ruby
func is_long_prime(p) {
 
    for d in (divisors(p-1)) {
        if (powmod(10, d, p) == 1) {
            return (d+1 == p)
        }
    }
 
    return false
}
 
say "Long primes ≤ 500:"
say primes(500).grep(is_long_prime).join(' ')
 
for n in ([500, 1000, 2000, 4000, 8000, 16000, 32000, 64000]) {
    say ("Number of long primes ≤ #{n}: ", primes(n).count_by(is_long_prime))
}
```

#### Output:
```
Long primes ≤ 500:
7 17 19 23 29 47 59 61 97 109 113 131 149 167 179 181 193 223 229 233 257 263 269 313 337 367 379 383 389 419 433 461 487 491 499
Number of long primes ≤ 500: 35
Number of long primes ≤ 1000: 60
Number of long primes ≤ 2000: 116
Number of long primes ≤ 4000: 218
Number of long primes ≤ 8000: 390
Number of long primes ≤ 16000: 716
Number of long primes ≤ 32000: 1300
Number of long primes ≤ 64000: 2430
```


Alternatively, we can implement the *is\_long\_prime(p)* function using the \`znorder(a, p)\` built-in method, which is considerably faster:

```ruby
func is_long_prime(p) {
    znorder(10, p) == p-1
}
```