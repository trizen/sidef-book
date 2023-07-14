[1]: https://rosettacode.org/wiki/Sorting_algorithms/Pancake_sort

# [Sorting algorithms/Pancake sort][1]

```ruby
func pancake(a) {
    for idx in ^(a.end) {
        var min = idx
        for i in (idx+1 .. a.end) { min = i if (a[min] > a[i]) }
        next if (a[min] == a[idx])
        a[min..a.end] = [a[min..a.end]].reverse...
        a[idx..a.end] = [a[idx..a.end]].reverse...
    }
    return a
}

var arr = 10.of{ 100.irand }
say "Before: #{arr}"
say "After:  #{pancake(arr)}"
```

#### Output:
```
Before: 61 29 68 15 34 2 32 54 73 43
After:  2 15 29 32 34 43 54 61 68 73
```
