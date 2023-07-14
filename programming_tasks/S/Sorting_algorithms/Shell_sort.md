[1]: https://rosettacode.org/wiki/Sorting_algorithms/Shell_sort

# [Sorting algorithms/Shell sort][1]

```ruby
func shell_sort(a) {
    var h = a.len
    while (h >>= 1) {
        for i in (h .. a.end) {
            var k = a[i]
            for (var j = i; (j >= h) && (k < a[j - h]); j -= h) {
                a[j] = a[j - h]
            }
            a[j] = k
        }
    }
    return a
}

var a = rand(1..100, 10)
say a
shell_sort(a)
say a
```

#### Output:
```
[54, 67, 65, 8, 56, 83, 64, 42, 20, 17]
[8, 17, 20, 42, 54, 56, 64, 65, 67, 83]
```
