[1]: https://rosettacode.org/wiki/Pell_numbers

# [Pell numbers][1]

```ruby
func pell_number(n) {
    lucasU(2, -1, n)
}

func pell_lucas_number(n) {
    lucasV(2, -1, n)
}

say ("The first 10 Pell numbers: ", 10.of(pell_number).join(", "))
say ("The first 10 Pell-Lucas numbers: ", 10.of(pell_lucas_number).join(", "))

say "\nFirst 10 rational approximations to √2:"
{|n| pell_lucas_number(n) / 2 / pell_number(n) }.map(1..10).each {|r|
    say "#{'%10s' % r.as_frac} =~ #{r.as_float}"
}

var pell_prime_indices = 10.by {|n| pell_number(n).is_prime }
say "\nThe first 10 Pell primes: "
pell_prime_indices.each {|n|
    say "Pell(#{'%2s' % n}) = #{pell_number(n)}"
}

say ("\nThe first 10 Newman-Shank-Williams numbers: ",
    10.of{|n| pell_number(2*n) + pell_number(2*n + 1) }.join(', '))

say "\nThe first 10 Pythagorean triples corresponding to near isosceles right triangles:"
10.of{|n| pell_number(2*n + 1) }.map {|h|
    var t = isqrt(h**2 >> 1)
    assert_eq(t**2 + (t+1)**2, h**2)
    [t, t+1, h]
}.each{.say}
```

#### Output:
```
The first 10 Pell numbers: 0, 1, 2, 5, 12, 29, 70, 169, 408, 985
The first 10 Pell-Lucas numbers: 2, 2, 6, 14, 34, 82, 198, 478, 1154, 2786

First 10 rational approximations to √2:
       1/1 =~ 1
       3/2 =~ 1.5
       7/5 =~ 1.4
     17/12 =~ 1.41666666666666666666666666666666666666666666667
     41/29 =~ 1.41379310344827586206896551724137931034482758621
     99/70 =~ 1.41428571428571428571428571428571428571428571429
   239/169 =~ 1.41420118343195266272189349112426035502958579882
   577/408 =~ 1.4142156862745098039215686274509803921568627451
  1393/985 =~ 1.41421319796954314720812182741116751269035532995
 3363/2378 =~ 1.41421362489486963835155592935239697224558452481

The first 10 Pell primes: 
Pell( 2) = 2
Pell( 3) = 5
Pell( 5) = 29
Pell(11) = 5741
Pell(13) = 33461
Pell(29) = 44560482149
Pell(41) = 1746860020068409
Pell(53) = 68480406462161287469
Pell(59) = 13558774610046711780701
Pell(89) = 4125636888562548868221559797461449

The first 10 Newman-Shank-Williams numbers: 1, 7, 41, 239, 1393, 8119, 47321, 275807, 1607521, 9369319

The first 10 Pythagorean triples corresponding to near isosceles right triangles:
[0, 1, 1]
[3, 4, 5]
[20, 21, 29]
[119, 120, 169]
[696, 697, 985]
[4059, 4060, 5741]
[23660, 23661, 33461]
[137903, 137904, 195025]
[803760, 803761, 1136689]
[4684659, 4684660, 6625109]
```
