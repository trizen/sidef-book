[1]: https://rosettacode.org/wiki/Extra_primes

# [Extra primes][1]

Simple solution:

```ruby
say 1e4.primes.grep { .digits.all { .is_prime } && .sumdigits.is_prime }
```

#### Output:
```
[2, 3, 5, 7, 23, 223, 227, 337, 353, 373, 557, 577, 733, 757, 773, 2333, 2357, 2377, 2557, 2753, 2777, 3253, 3257, 3323, 3527, 3727, 5233, 5237, 5273, 5323, 5527, 7237, 7253, 7523, 7723, 7727]
```


Generate such primes from digits (faster):

```ruby
func extra_primes(upto, base = 10) {
 
    upto = prev_prime(upto+1)
 
    var list = []
    var digits = @(^base)
 
    var prime_digits = digits.grep { .is_prime }
    var end_digits   = prime_digits.grep { .is_coprime(base) }
 
    list << prime_digits.grep { !.is_coprime(base) }...
 
    for k in (0 .. upto.ilog(base)) {
        prime_digits.variations_with_repetition(k, {|*a|
            next if ([end_digits[0], a...].digits2num(base) > upto)
            end_digits.each {|d|
                var n = [d, a...].digits2num(base)
                list << n if (n.is_prime && n.sumdigits(base).is_prime)
            }
        })
    }
 
    list.sort
}
 
with (1e4) { |n|
    say "Extra primes <= #{n.commify}:"
    say extra_primes(n).join(' ')
}
 
with (1000000000) {|n|
    say "\nLast 10 extra primes <= #{n.commify}:"
    say extra_primes(n).last(10).join(' ')
}
```

#### Output:
```
Extra primes <= 10,000:
2 3 5 7 23 223 227 337 353 373 557 577 733 757 773 2333 2357 2377 2557 2753 2777 3253 3257 3323 3527 3727 5233 5237 5273 5323 5527 7237 7253 7523 7723 7727

Last 10 extra primes <= 1,000,000,000:
777753773 777755753 777773333 777773753 777775373 777775553 777775577 777777227 777777577 777777773
```
