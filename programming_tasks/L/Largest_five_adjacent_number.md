[1]: https://rosettacode.org/wiki/Largest_five_adjacent_number

# [Largest five adjacent number][1]

```ruby
var k = 5
var n = 1e1000.irand
 
say "length(n) = #{n.len}"
 
var c = n.digits.cons(k)
 
say ("Min #{k}-digit sub-number: ", c.min_by { .digits2num }.flip.join)
say ("Max #{k}-digit sub-number: ", c.max_by { .digits2num }.flip.join)
```

#### Output:
```
length(n) = 1000
Min 5-digit sub-number: 00072
Max 5-digit sub-number: 99861
```
