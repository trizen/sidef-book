[1]: https://rosettacode.org/wiki/Pseudo-random_numbers/Middle-square_method

# [Pseudo-random numbers/Middle-square method][1]

```ruby
class MiddleSquareMethod(seed, k = 1000) {
    method next {
        seed = (seed**2 // k % k**2)
    }
}
 
var obj = MiddleSquareMethod(675248)
say 5.of { obj.next }
```

#### Output:
```
[959861, 333139, 981593, 524817, 432883]
```
