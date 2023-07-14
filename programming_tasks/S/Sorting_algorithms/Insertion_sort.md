[1]: https://rosettacode.org/wiki/Sorting_algorithms/Insertion_sort

# [Sorting algorithms/Insertion sort][1]

```ruby
class Array {
    method insertion_sort {
        { |i|
            var j = i-1
            var k = self[i]
            while ((j >= 0) && (k < self[j])) {
                self[j+1] = self[j]
                j--
            }
            self[j+1] = k
        } << 1..self.end
        return self
    }
}

var a = 10.of { 100.irand }
say a.insertion_sort
```
