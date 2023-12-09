[1]: https://rosettacode.org/wiki/Primes_with_digits_in_nondecreasing_order

# [Primes with digits in nondecreasing order][1]

Simple solution:

```ruby
say 1000.primes.grep { .digits.cons(2).all { .head >= .tail } }
```


Generate such primes from digits (asymptotically faster):

```ruby
func primes_with_nondecreasing_digits(upto, base = 10) {

    upto = prev_prime(upto+1)

    var list = []
    var digits = @(1..^base -> flip)

    var end_digits = digits.grep { .is_coprime(base) }
    list << digits.grep { .is_prime && !.is_coprime(base) }...

    for k in (0 .. upto.ilog(base)) {
        digits.combinations_with_repetition(k, {|*a|
            var v = a.digits2num(base)
            next if (v*base + end_digits.tail > upto)
            end_digits.each {|d|
                var n = (v*base + d)
                next if ((n >= base) && (a[0] > d))
                list << n if n.is_prime
            }
        })
    }

    list.sort
}

say primes_with_nondecreasing_digits(1000)
```

#### Output:
```
[2, 3, 5, 7, 11, 13, 17, 19, 23, 29, 37, 47, 59, 67, 79, 89, 113, 127, 137, 139, 149, 157, 167, 179, 199, 223, 227, 229, 233, 239, 257, 269, 277, 337, 347, 349, 359, 367, 379, 389, 449, 457, 467, 479, 499, 557, 569, 577, 599, 677]
```
