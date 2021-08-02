[1]: https://rosettacode.org/wiki/Primes_which_contain_only_one_odd_number

# [Primes which contain only one odd number][1]

```ruby
func primes_with_one_odd_digit(upto, base = 10) {

    var list = []
    var digits = @(^base)

    var even_digits = digits.grep { .is_even }
    var odd_digits  = digits.grep { .is_odd && .is_coprime(base) }

    list << digits.grep { .is_odd && .is_prime && !.is_coprime(base) }...

    for k in (0 .. upto.len(base)-1) {
        even_digits.variations_with_repetition(k, {|*a|
            next if (a.last == 0)
            break if ([1, a...].digits2num(base) > upto)
            odd_digits.each {|d|
                var n = [d, a...].digits2num(base)
                list << n if n.is_prime
            }
        })
    }

    list.sort
}

with (1e3) {|n|
    var list = primes_with_one_odd_digit(n)
    say "There are #{list.len} primes under #{n.commify} which contain only one odd digit:"
    list.each_slice(9, {|*a| say a.map { '%3s' % _ }.join(' ') })
}

say ''

for k in (1..8) {
    var count = primes_with_one_odd_digit(10**k).len
    say "There are #{'%6s' % count.commify} such primes <= 10^#{k}"
}
```

#### Output:
```
There are 45 primes under 1,000 which contain only one odd digit:
  3   5   7  23  29  41  43  47  61
 67  83  89 223 227 229 241 263 269
281 283 401 409 421 443 449 461 463
467 487 601 607 641 643 647 661 683
809 821 823 827 829 863 881 883 887

There are      3 such primes <= 10^1
There are     12 such primes <= 10^2
There are     45 such primes <= 10^3
There are    171 such primes <= 10^4
There are    619 such primes <= 10^5
There are  2,560 such primes <= 10^6
There are 10,774 such primes <= 10^7
There are 46,708 such primes <= 10^8
```