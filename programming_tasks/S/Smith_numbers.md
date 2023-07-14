[1]: https://rosettacode.org/wiki/Smith_numbers

# [Smith numbers][1]

```ruby
var primes = Enumerator({ |callback|
    static primes = Hash()
    var p = 2
    loop {
        callback(p)
        p = (primes{p} := p.next_prime)
    }
})
 
func factors(remainder) {
 
    remainder == 1 && return([remainder])
 
    gather {
        primes.each { |factor|
            if (factor*factor > remainder) {
                take(remainder) if (remainder > 1)
                break
            }
 
            while (factor.divides(remainder)) {
                take(factor)
                break if ((remainder /= factor) == 1)
            }
        }
    }
}
 
func is_smith_number(n) {
    !n.is_prime && (n.sumdigits == factors(n).join.to_i.sumdigits)
}
 
var s = range(2, 10_000).grep { is_smith_number(_) }
say "#{s.len} Smith numbers below 10_000"
say "First 10: #{s.first(10)}"
say "Last  10: #{s.last(10)}"
```

#### Output:
```
376 Smith numbers below 10_000
First 10: [4, 22, 27, 58, 85, 94, 121, 166, 202, 265]
Last  10: [9843, 9849, 9861, 9880, 9895, 9924, 9942, 9968, 9975, 9985]
```
