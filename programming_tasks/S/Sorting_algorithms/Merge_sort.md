[1]: http://rosettacode.org/wiki/Sorting_algorithms/Merge_sort

# [Sorting algorithms/Merge sort][1]

```ruby
func merge(left, right) {
    var result = [];
    while (!left.is_empty && !right.is_empty) {
        result.append([right,left][left.first <= right.first].shift);
    };
    result + left + right;
}
 
func mergesort(array) {
    var len = array.len
            < 2 && return array;
 
    var mid   = (len/2 int);
    var left  = array.ft(0, mid-1);
    var right = array.ft(mid);
 
    left  = __FUNC__(left);
    right = __FUNC__(right);
 
    merge(left, right);
}
 
# Numeric sort
var nums = (0..7 shuffle);
mergesort(nums).dump.say;
 
# String sort
var strings = ('a'..'e' shuffle);
mergesort(strings).dump.say;
```

#### Output:
```
[0, 1, 2, 3, 4, 5, 6, 7]
['a', 'b', 'c', 'd', 'e']
```