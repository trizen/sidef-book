[1]: http://rosettacode.org/wiki/Factors_of_an_integer

# [Factors of an integer][1]

```ruby
func factors(n) {
  gather {
    { |d|
        take(d, n//d) if d.divides(n)
    } << 1..n.isqrt
  }.sort.uniq
}
 
for n [53, 64, 32766] {
    say "factors(#{n}): #{factors(n)}"
}
```

#### Output:
```
factors(53): 1 53
factors(64): 1 2 4 8 16 32 64
factors(32766): 1 2 3 6 43 86 127 129 254 258 381 762 5461 10922 16383 32766
```
