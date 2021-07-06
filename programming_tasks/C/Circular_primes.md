[1]: https://rosettacode.org/wiki/Circular_primes

# [Circular primes][1]

```ruby
func is_circular_prime(n) {
    n.is_prime || return false
 
    var circular = n.digits
    circular.min < circular.tail && return false
 
    for k in (1 ..^ circular.len) {
        with (circular.rotate(k).digits2num) {|p|
            (p.is_prime && (p >= n)) || return false
        }
    }
 
    return true
}
 
say "The first 19 circular primes are:"
say 19.by(is_circular_prime)
 
say "\nThe next 4 circular primes, in repunit format, are:"
{|n| (10**n - 1)/9 -> is_prob_prime }.first(4, 4..Inf).each {|n|
    say "R(#{n})"
}
 
say "\nRepunit testing:"
[5003, 9887, 15073, 25031, 35317, 49081].each {|n|
    var now = Time.micro
    say ("R(#{n}) -> ", is_prob_prime((10**n - 1)/9) ? 'probably prime' : 'composite',
        " (took: #{'%.3f' % Time.micro-now} sec)")
}
```

#### Output:
```
The first 19 circular primes are:
[2, 3, 5, 7, 11, 13, 17, 37, 79, 113, 197, 199, 337, 1193, 3779, 11939, 19937, 193939, 199933]

The next 4 circular primes, in repunit format, are:
R(19)
R(23)
R(317)
R(1031)

Repunit testing:
R(5003) -> composite (took: 0.024 sec)
R(9887) -> composite (took: 0.006 sec)
R(15073) -> composite (took: 0.389 sec)
R(25031) -> composite (took: 54.452 sec)
R(35317) -> composite (took: 0.875 sec)
```
