[1]: http://rosettacode.org/wiki/Sorting_algorithms/Counting_sort

# [Sorting algorithms/Counting sort][1]

```ruby
func counting_sort(a, min, max) {
    var cnt = ([0] * (max - min + 1));
    a.each { |i| cnt[i-min]++ };
    return cnt.map {|i| min++; [min-1] * i}.sum;
}
 
var a = 100.of {100.rand.int};
say counting_sort(a, 0, 100).dump;
```