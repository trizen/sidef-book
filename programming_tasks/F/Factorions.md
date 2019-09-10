[1]: https://rosettacode.org/wiki/Factorions

# [Factorions][1]

```ruby
func max_power(b = 10) {
    var m = 1
    var f = (b-1)!
    while (m*f >= b**(m-1)) {
        m += 1
    }
    return m-1
}
 
func factorions(b = 10) {
 
    var result = []
    var digits = @^b
    var fact = digits.map { _! }
 
    for k in (1 .. max_power(b)) {
        digits.combinations_with_repetition(k, {|*comb|
            var n = comb.sum_by { fact[_] }
            if (n.digits(b).sort == comb) {
                result << n
            }
        })
    }
 
    return result
}
 
for b in (2..12) {
    var r = factorions(b)
    say "Base #{'%2d' % b} factorions: #{r}"
}
```

#### Output:
```
Base  2 factorions: [1, 2]
Base  3 factorions: [1, 2]
Base  4 factorions: [1, 2, 7]
Base  5 factorions: [1, 2, 49]
Base  6 factorions: [1, 2, 25, 26]
Base  7 factorions: [1, 2]
Base  8 factorions: [1, 2]
Base  9 factorions: [1, 2, 41282]
Base 10 factorions: [1, 2, 145, 40585]
Base 11 factorions: [1, 2, 26, 48, 40472]
Base 12 factorions: [1, 2]
```
