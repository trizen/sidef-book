[1]: https://rosettacode.org/wiki/Twin_primes

# [Twin primes][1]

```ruby
func twin_primes_count(upto) {
    var count = 0
    var p1 = 2
    each_prime(3, upto, {|p2|
        if (p2 - p1 == 2) {
            ++count
        }
        p1 = p2
    })
    return count
}
 
for n in (1..9) {
    var count = twin_primes_count(10**n)
    say "There are #{count} twin primes <= 10^#{n}"
}
```

#### Output:
```
There are 2 twin primes <= 10^1
There are 8 twin primes <= 10^2
There are 35 twin primes <= 10^3
There are 205 twin primes <= 10^4
There are 1224 twin primes <= 10^5
There are 8169 twin primes <= 10^6
There are 58980 twin primes <= 10^7
There are 440312 twin primes <= 10^8
There are 3424506 twin primes <= 10^9
```
