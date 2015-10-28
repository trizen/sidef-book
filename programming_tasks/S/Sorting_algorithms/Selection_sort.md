[1]: http://rosettacode.org/wiki/Sorting_algorithms/Selection_sort

# [Sorting algorithms/Selection sort][1]

```ruby
class Array {
    method selectionsort {
        range(0, self.len-2).each { |i|
            var min_idx = i;
            range(i+1, self.len-1).each { |j|
                self[j] < self[min_idx] && (
                    min_idx = j;
                )
            }
            self[i, min_idx] = self[min_idx, i];
        }
        return self;
    }
}
 
var nums = [7,6,5,9,8,4,3,1,2,0];
say nums.selectionsort;
 
var strs = ["John", "Kate", "Zerg", "Alice", "Joe", "Jane"];
say strs.selectionsort;
```