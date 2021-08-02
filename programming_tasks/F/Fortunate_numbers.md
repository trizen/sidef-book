[1]: https://rosettacode.org/wiki/Fortunate_numbers

# [Fortunate numbers][1]

```ruby
func fortunate(n) {
    var P = n.pn_primorial
    2..Inf -> first {|m| P+m -> is_prob_prime }
}
 
var limit = 50
var uniq = Set()
var all = []
 
for (var n = 1; uniq.len < 2*limit; ++n) {
    var m = fortunate(n)
    all << m
    uniq << m
}
 
say "Fortunate numbers for n = 1..#{limit}:"
say all.first(limit)
 
say "\n#{limit} Fortunate numbers, sorted with duplicates removed:"
say uniq.sort.first(limit)
```

#### Output:
```
Fortunate numbers for n = 1..50:
[3, 5, 7, 13, 23, 17, 19, 23, 37, 61, 67, 61, 71, 47, 107, 59, 61, 109, 89, 103, 79, 151, 197, 101, 103, 233, 223, 127, 223, 191, 163, 229, 643, 239, 157, 167, 439, 239, 199, 191, 199, 383, 233, 751, 313, 773, 607, 313, 383, 293]

50 Fortunate numbers, sorted with duplicates removed:
[3, 5, 7, 13, 17, 19, 23, 37, 47, 59, 61, 67, 71, 79, 89, 101, 103, 107, 109, 127, 151, 157, 163, 167, 191, 197, 199, 223, 229, 233, 239, 271, 277, 283, 293, 307, 311, 313, 331, 353, 373, 379, 383, 397, 401, 409, 419, 421, 439, 443]
```
