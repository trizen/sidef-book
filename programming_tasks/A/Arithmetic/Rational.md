[1]: https://rosettacode.org/wiki/Arithmetic/Rational

# [Arithmetic/Rational][1]

Sidef has built-in support for rational numbers.

```ruby
for n in (1 .. 2**19) {
    var frac = 0
 
    n.divisors.each {|d|
        frac += 1/d
    }
 
    if (frac.is_int) {
        say "Sum of reciprocal divisors of #{n} = #{frac} exactly #{
            frac == 2 ? '- perfect!' : ''
        }"
    }
}
```

#### Output:
```
Sum of reciprocal divisors of 1 = 1 exactly 
Sum of reciprocal divisors of 6 = 2 exactly - perfect!
Sum of reciprocal divisors of 28 = 2 exactly - perfect!
Sum of reciprocal divisors of 120 = 3 exactly 
Sum of reciprocal divisors of 496 = 2 exactly - perfect!
Sum of reciprocal divisors of 672 = 3 exactly 
Sum of reciprocal divisors of 8128 = 2 exactly - perfect!
Sum of reciprocal divisors of 30240 = 4 exactly 
Sum of reciprocal divisors of 32760 = 4 exactly 
Sum of reciprocal divisors of 523776 = 3 exactly 
```