[1]: https://rosettacode.org/wiki/Primes_whose_first_and_last_number_is_3

# [Primes whose first and last number is 3][1]

```ruby
func numbers_with_edges(upto, base = 10, s = [3]) {
    Enumerator({|callback|
        callback(s.digits2num(base))
        for k in (0 .. base**(upto.len(base) - 2*s.len)) {
 
            break if (s + k.digits(base) + s -> digits2num(base) > upto)
 
            Inf.times { |j|
 
                var d = (s + k.digits(base) + j.of(0) + s)
                var n = d.digits2num(base)
 
                (n <= upto) ? callback(n) : break
            }
        }
    })
}
 
with (4e3) { |n|
    var list  = numbers_with_edges(n).grep{.is_prime}.sort
    say "There are #{list.len} primes <= #{n.commify} which begin and end in 3:"
    list.each_slice(10, {|*a| say a.map { '%5s' % _ }.join(' ') })
}
 
with (1e6) {|n|
    var count = numbers_with_edges(n).grep{.is_prime}.len
    say "\nThere are #{count} primes <= #{n.commify} which begin and end in 3"
}
```

#### Output:
```
There are 33 primes <= 4,000 which begin and end in 3:
    3   313   353   373   383  3023  3083  3163  3203  3253
 3313  3323  3343  3373  3413  3433  3463  3533  3583  3593
 3613  3623  3643  3673  3733  3793  3803  3823  3833  3853
 3863  3923  3943

There are 2251 primes <= 1,000,000 which begin and end in 3
```
