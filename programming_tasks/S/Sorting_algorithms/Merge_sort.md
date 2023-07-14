[1]: https://rosettacode.org/wiki/Sorting_algorithms/Merge_sort

# [Sorting algorithms/Merge sort][1]

```ruby
func merge(left, right) {
    var result = []
    while (left && right) {
        result << [right,left].min_by{.first}.shift
    }
    result + left + right
}
 
func mergesort(array) {
    var len = array.len
    len < 2 && return array
 
    var (left, right) = array.part(len//2)
 
    left  = __FUNC__(left)
    right = __FUNC__(right)
 
    merge(left, right)
}
 
# Numeric sort
var nums = rand(1..100, 10)
say mergesort(nums)
 
# String sort
var strings = rand('a'..'z', 10)
say mergesort(strings)
```

#### Output:
```
[0, 1, 2, 3, 4, 5, 6, 7]
['a', 'b', 'c', 'd', 'e']
```
