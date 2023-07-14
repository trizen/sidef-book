[1]: https://rosettacode.org/wiki/Sorting_algorithms/Bubble_sort

# [Sorting algorithms/Bubble sort][1]

```ruby
func bubble_sort(arr) {
    loop {
        var swapped = false
        { |i|
            if (arr[i] > arr[i+1]) {
                arr[i, i+1] = arr[i+1, i]
                swapped = true
            }
        } << ^arr.end
        swapped || break
    }
    return arr
}
```
