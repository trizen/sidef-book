[1]: https://rosettacode.org/wiki/Sorting_algorithms/Comb_sort

# [Sorting algorithms/Comb sort][1]

```ruby
func comb_sort(arr) {
    var gap = arr.len
    var swaps = true
    while (gap > 1 || swaps) {
        gap.div!(1.25).int! if (gap > 1)
        swaps = false
        for i in ^(arr.len - gap) {
            if (arr[i] > arr[i+gap]) {
                arr[i, i+gap] = arr[i+gap, i]
                swaps = true
            }
        }
    }
    return arr
}
```
