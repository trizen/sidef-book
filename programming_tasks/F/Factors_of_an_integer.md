[1]: http://rosettacode.org/wiki/Factors_of_an_integer

# [Factors of an integer][1]

```ruby
func factors(n) {
  var divs = []
  range(1, n.sqrt.int).each { |d|
    divs << d if d.divides(n)
  }
  divs + [divs[-1]**2 == n ? divs.pop : ()] + divs.reverse.map{|d| n/d }
}
 
[53, 64, 32766].each { |n|
    say "factors(#{n}): #{factors(n)}"
}
```

#### Output:
```
factors(53): 1 53
factors(64): 1 2 4 8 16 32 64
factors(32766): 1 2 3 6 43 86 127 129 254 258 381 762 5461 10922 16383 32766
```
