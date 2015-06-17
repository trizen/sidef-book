[1]: http://rosettacode.org/wiki/Sorting_algorithms/Insertion_sort

# [Sorting algorithms/Insertion sort][1]

```ruby
class Array {
    method insertion_sort {
        { |i|
            var j = i;
            var k = self[i];
            while ((j > 0) && (k < self[j - 1])) {
                self[j] = self[j - 1];
                j--;
            };
            self[j] = k;
        } * self.offset;
        return self;
    }
}
 
var a = 10.of {100.rand.int};
say a.insertion_sort.dump;
```