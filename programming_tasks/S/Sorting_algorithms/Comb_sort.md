[1]: http://rosettacode.org/wiki/Sorting_algorithms/Comb_sort

# [Sorting algorithms/Comb sort][1]

```ruby
func combSort(arr is Array) {
    var gap = arr.len;
    var swaps = true;
    while (gap > 1 || swaps) {
        {gap.div!(1.25).int!} if (gap > 1);
        swaps = false;
        0 to (arr.end - gap) -> each { |i|
            if (arr[i] > arr[i+gap]) {
                arr[i, i+gap] = arr[i+gap, i];
                swaps = true;
            }
        }
    };
    return arr;
};
```