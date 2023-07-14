[1]: https://rosettacode.org/wiki/Sorting_Algorithms/Circle_Sort

# [Sorting Algorithms/Circle Sort][1]

```ruby
func circlesort(arr, beg=0, end=arr.end) {
    var swaps = 0
    if (beg < end) {
        var (lo, hi) = (beg, end)
        do {
            if (arr[lo] > arr[hi]) {
                arr.swap(lo, hi)
                ++swaps
            }
            ++hi if (--hi == ++lo)
        } while (lo < hi)
        swaps += circlesort(arr, beg, hi)
        swaps += circlesort(arr, lo, end)
    }
    return swaps
}
 
var numbers = %n(2 3 3 5 5 1 1 7 7 6 6 4 4 0 0)
do { say numbers } while circlesort(numbers)
 
var strs = ["John", "Kate", "Zerg", "Alice", "Joe", "Jane", "Alice"]
do { say strs } while circlesort(strs)
```

#### Output:
```
[2, 3, 3, 5, 5, 1, 1, 7, 7, 6, 6, 4, 4, 0, 0]
[0, 0, 1, 4, 1, 5, 3, 7, 2, 3, 4, 5, 6, 6, 7]
[0, 0, 1, 1, 2, 3, 3, 4, 4, 5, 5, 7, 6, 6, 7]
[0, 0, 1, 1, 2, 3, 3, 4, 4, 5, 5, 6, 6, 7, 7]
["John", "Kate", "Zerg", "Alice", "Joe", "Jane", "Alice"]
["Alice", "Jane", "Alice", "Joe", "John", "Kate", "Zerg"]
["Alice", "Alice", "Jane", "Joe", "John", "Kate", "Zerg"]
```