[1]: https://rosettacode.org/wiki/Proper_divisors

# [Proper divisors][1]

```ruby
func propdiv (n) {
    n.divisors.slice(0, -2)
}

{|i| printf("%2d: %s\n", i, propdiv(i)) } << 1..10

var max = 0
var candidates = []

for i in (1..20_000) {
    var divs = propdiv(i).len
    if (divs > max) {
        candidates = []
        max = divs
    }
    candidates << i if (divs == max)
}

say "max = #{max}, candidates = #{candidates}"
```

#### Output:
```
 1: []
 2: [1]
 3: [1]
 4: [1, 2]
 5: [1]
 6: [1, 2, 3]
 7: [1]
 8: [1, 2, 4]
 9: [1, 3]
10: [1, 2, 5]
max = 79, candidates = [15120, 18480]
```
