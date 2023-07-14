[1]: https://rosettacode.org/wiki/Sort_disjoint_sublist

# [Sort disjoint sublist][1]

```ruby
func disjointSort(values, indices) {
    values[indices.sort] = [values[indices]].sort...
}

var values =  [7, 6, 5, 4, 3, 2, 1, 0]
var indices = [6, 1, 7]

disjointSort(values, indices)
say values
```

#### Output:
```
[7, 0, 5, 4, 3, 2, 1, 6]
```
