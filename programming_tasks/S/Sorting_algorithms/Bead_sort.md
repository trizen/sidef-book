[1]: https://rosettacode.org/wiki/Sorting_algorithms/Bead_sort

# [Sorting algorithms/Bead sort][1]

```ruby
func beadsort(arr) {

    var rows = []
    var columns = []

    for datum in arr {
        for column in ^datum {
            ++(columns[column] := 0)
            ++(rows[columns[column] - 1] := 0)
        }
    }

    rows.reverse
}

say beadsort([5,3,1,7,4,1,1])
```

#### Output:
```
[1, 1, 1, 3, 4, 5, 7]
```
