[1]: http://rosettacode.org/wiki/Sorting_algorithms/Bogosort

# [Sorting algorithms/Bogosort][1]

```ruby
func in_order(a) {
    return true if (a.len <= 1)
    var first = a[0]
    a.last(-1).all { |elem| first <= elem  ? do { first = elem; true } : false }
}

func bogosort(a) {
    a.shuffle! while !in_order(a)
    return a
}

var arr = 5.of { 100.irand }
say "Before: #{arr}"
say "After:  #{bogosort(arr)}"
```

#### Output:
```
Before: 57 45 83 85 33
After:  33 45 57 83 85
```
