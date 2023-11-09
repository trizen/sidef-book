[1]: https://rosettacode.org/wiki/Descending_primes

# [Descending primes][1]

```ruby
func primes_with_descending_digits(base = 10) {
 
    var list = []
    var digits = @(1..^base)
 
    var end_digits = digits.grep { .is_coprime(base) }
    list << digits.grep { .is_prime && !.is_coprime(base) }...
 
    for k in (0 .. digits.end) {
        digits.combinations(k, {|*a|
            var v = a.digits2num(base)
            end_digits.each {|d|
                var n = (v*base + d)
                next if ((n >= base) && (a[0] <= d))
                list << n if n.is_prime
            }
        })
    }
 
    list.sort
}
 
var base = 10
var arr = primes_with_descending_digits(base)
 
say "There are #{arr.len} descending primes in base #{base}.\n"
 
arr.each_slice(8, {|*a|
    say a.map { '%9s' % _ }.join(' ')
})
```

#### Output:
```
There are 87 descending primes in base 10.

        2         3         5         7        31        41        43        53
       61        71        73        83        97       421       431       521
      541       631       641       643       653       743       751       761
      821       853       863       941       953       971       983      5431
     6421      6521      7321      7541      7621      7643      8431      8521
     8543      8641      8731      8741      8753      8761      9421      9431
     9521      9631      9643      9721      9743      9851      9871     75431
    76421     76541     76543     86531     87421     87541     87631     87641
    87643     94321     96431     97651     98321     98543     98621     98641
    98731    764321    865321    876431    975421    986543    987541    987631
  8764321   8765321   9754321   9875321  97654321  98764321  98765431
```