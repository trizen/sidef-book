[1]: https://rosettacode.org/wiki/Palindromic_primes_in_base_16

# [Palindromic primes in base 16][1]

```ruby
func palindromic_primes(upto, base = 10) {
    var list = []
    for (var p = 2; p <= upto; p = p.next_palindrome(base)) {
        list << p if p.is_prime
    }
    return list
}
 
var list = palindromic_primes(500, 16)
 
list.each {|p|
    say "#{'%3s' % p}_10 = #{'%3s' % p.base(16)}_16"
}
```

#### Output:
```
  2_10 =   2_16
  3_10 =   3_16
  5_10 =   5_16
  7_10 =   7_16
 11_10 =   b_16
 13_10 =   d_16
 17_10 =  11_16
257_10 = 101_16
337_10 = 151_16
353_10 = 161_16
401_10 = 191_16
433_10 = 1b1_16
449_10 = 1c1_16
```
