[1]: https://rosettacode.org/wiki/Sorting_algorithms/Stooge_sort

# [Sorting algorithms/Stooge sort][1]

```ruby
func stooge(x, i, j) {
    if (x[j] < x[i]) {
        x.swap(i, j)
    }

    if (j-i > 1) {
        var t = ((j - i + 1) / 3)
        stooge(x, i,     j - t)
        stooge(x, i + t, j    )
        stooge(x, i,     j - t)
    }
}

var a = 10.of { 100.irand }

say "Before #{a}"
stooge(a, 0, a.end)
say "After  #{a}"
```
