[1]: https://rosettacode.org/wiki/Sorting_algorithms/Selection_sort

# [Sorting algorithms/Selection sort][1]

```ruby
class Array {
    method selectionsort {
        for i in ^(self.end) {
            var min_idx = i
            for j in (i+1 .. self.end) {
                if (self[j] < self[min_idx]) {
                    min_idx = j
                }
            }
            self.swap(i, min_idx)
        }
        return self
    }
}

var nums = [7,6,5,9,8,4,3,1,2,0]
say nums.selectionsort

var strs = ["John", "Kate", "Zerg", "Alice", "Joe", "Jane"]
say strs.selectionsort
```
