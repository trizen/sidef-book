[1]: https://rosettacode.org/wiki/Primes_which_sum_of_digits_is_25

# [Primes which sum of digits is 25][1]

Simple solution:

```ruby
5000.primes.grep { .sumdigits == 25 }.say
```


Generate such primes from digits (asymptotically faster):

```ruby
func generate_from_prefix(limit, digitsum, p, base, digits, t=p) {
 
    var seq = [p]
 
    digits.each {|d|
        var num = (p*base + d)
        num <= limit    || return seq
 
        var sum = (t + d)
        sum <= digitsum || return seq
 
        seq << __FUNC__(limit, digitsum, num, base, digits, sum)\
               .grep { .is_prime }...
    }
 
    return seq
}
 
func primes_with_digit_sum(limit, digitsum = 25, base = 10, digits = @(^base)) {
    digits.grep { _ > 0 }\
          .map  { generate_from_prefix(limit, digitsum, _, base, digits)... }\
          .grep { .sumdigits(base) == digitsum }\
          .sort
}
 
say primes_with_digit_sum(5000)
```

#### Output:
```
[997, 1699, 1789, 1879, 1987, 2689, 2797, 2887, 3499, 3697, 3769, 3877, 3967, 4597, 4759, 4957, 4993]
```
