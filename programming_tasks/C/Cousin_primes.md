[1]: https://rosettacode.org/wiki/Cousin_primes

# [Cousin primes][1]

```ruby
var limit = 1000
var pairs = (limit-5).primes.map { [_, _+4] }.grep { .tail.is_prime }
 
say "Cousin prime pairs whose elements are less than #{limit.commify}:"
say pairs
say "\n#{pairs.len} pairs found"
```

#### Output:
```
Cousin prime pairs whose elements are less than 1,000:
[[3, 7], [7, 11], [13, 17], [19, 23], [37, 41], [43, 47], [67, 71], [79, 83], [97, 101], [103, 107], [109, 113], [127, 131], [163, 167], [193, 197], [223, 227], [229, 233], [277, 281], [307, 311], [313, 317], [349, 353], [379, 383], [397, 401], [439, 443], [457, 461], [463, 467], [487, 491], [499, 503], [613, 617], [643, 647], [673, 677], [739, 743], [757, 761], [769, 773], [823, 827], [853, 857], [859, 863], [877, 881], [883, 887], [907, 911], [937, 941], [967, 971]]

41 pairs found
```
