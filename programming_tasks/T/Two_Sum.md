[1]: http://rosettacode.org/wiki/Two_Sum

# [Two Sum][1]

```ruby
func two_sum(numbers, sum) {
    var (i, j) = (0, numbers.end)
    while (i < j) {
        given (sum <=> numbers[i]+numbers[j]) {
            when (-1) { --j }
            when (+1) { ++i }
            default { return [i, j] }
        }
    }
    return []
}
 
say two_sum([0, 2, 11, 19, 90], 21)
say two_sum([0, 2, 11, 19, 90], 25)
```

#### Output:
```
[1, 3]
[]
```