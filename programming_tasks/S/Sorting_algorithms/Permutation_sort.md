[1]: https://rosettacode.org/wiki/Sorting_algorithms/Permutation_sort

# [Sorting algorithms/Permutation sort][1]

```ruby
func psort(x, d=x.end) {
 
    if (d == 0) {
        for i in (1 .. x.end) {
            (x[i] < x[i-1]) && return false
        }
        return true
    }
 
    (d+1).times {
        x.prepend(x.splice(d, 1)...)
        x[d] < x[d-1] && next
        psort(x, d-1) && return true
    }
 
    return false
}
 
var a = 10.of { 100.irand }
say "Before:\t#{a}"
psort(a)
say "After:\t#{a}"
```

#### Output:
```
Before: 60 98 85 85 37 0 62 96 95 2
After:  0 2 37 60 62 85 85 95 96 98
```
