[1]: http://rosettacode.org/wiki/Sorting_algorithms/Cycle_sort

# [Sorting algorithms/Cycle sort][1]

```ruby
func cycle_sort (array) {
    var (writes=0, pos=0)
 
    func f(i, Ref item, bool=false) {
        pos = (i + array.ft(i+1).count{ _ < *item })
        return(false) if (bool && pos==i)
        while (*item == array[pos]) { ++pos }
        (array[pos], *item) = (*item, array[pos])
        ++writes
        return true
    }
 
    array.each_kv { |i, item|
        f(i, \item, true) || next
        while (pos != i) {
            f(i, \item)
        }
    }
 
    return writes
}
 
var a = %n(0 1 2 2 2 2 1 9 3.5 5 8 4 7 0 6)
 
say a.join(' ')
say ('writes ', cycle_sort(a))
say a.join(' ')
```

#### Output:
```
0 1 2 2 2 2 1 9 3.5 5 8 4 7 0 6
writes 10
0 0 1 1 2 2 2 2 3.5 4 5 6 7 8 9
```