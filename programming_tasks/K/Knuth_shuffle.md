[1]: http://rosettacode.org/wiki/Knuth_shuffle

# [Knuth shuffle][1]

```ruby
func knuth_shuffle(a) {
    for i (a.len ^.. 1) {
        var j = i.irand
        a[i, j] = a[j, i]
    }
    return a
}

say knuth_shuffle(@(1..10))
```

#### Output:
```
[5, 8, 4, 7, 10, 2, 9, 3, 1, 6]
```
