[1]: https://rosettacode.org/wiki/Palindromic_primes

# [Palindromic primes][1]

```ruby
func palindromic_primes(upto, base = 10) {
    var list = []
    for (var p = 2; p <= upto; p = p.next_palindrome(base)) {
        list << p if p.is_prime
    }
    return list
}
 
say palindromic_primes(1000)
 
for n in (1..10) {
    var count = palindromic_primes(10**n).len
    say "There are #{count} palindromic primes <= 10^#{n}"
}
```

#### Output:
```
[2, 3, 5, 7, 11, 101, 131, 151, 181, 191, 313, 353, 373, 383, 727, 757, 787, 797, 919, 929]
There are 4 palindromic primes <= 10^1
There are 5 palindromic primes <= 10^2
There are 20 palindromic primes <= 10^3
There are 20 palindromic primes <= 10^4
There are 113 palindromic primes <= 10^5
There are 113 palindromic primes <= 10^6
There are 781 palindromic primes <= 10^7
There are 781 palindromic primes <= 10^8
There are 5953 palindromic primes <= 10^9
There are 5953 palindromic primes <= 10^10
```
