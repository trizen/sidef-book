[1]: https://rosettacode.org/wiki/Permutation_test

# [Permutation test][1]

```ruby
func statistic(ab, a) {
    var(sumab, suma) = (ab.sum, a.sum)
    suma/a.size - ((sumab-suma) / (ab.size-a.size))
}
 
func permutationTest(a, b) {
    var ab = (a + b)
    var tobs = statistic(ab, a)
    var under = (var count = 0)
    ab.combinations(a.len, {|*perm|
        statistic(ab, perm) <= tobs && (under += 1)
        count += 1
    })
    under * 100 / count
}
 
var treatmentGroup = [85, 88, 75, 66, 25, 29, 83, 39, 97]
var controlGroup   = [68, 41, 10, 49, 16, 65, 32, 92, 28, 98]
var under = permutationTest(treatmentGroup, controlGroup)
say ("under=%.2f%%, over=%.2f%%" % (under, 100 - under))
```

#### Output:
```
under=87.20%, over=12.80%
```
