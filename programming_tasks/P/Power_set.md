[1]: https://rosettacode.org/wiki/Power_set

# [Power set][1]

```ruby
var arr = %w(a b c)
for i in (0 .. arr.len) {
    say arr.combinations(i)
}
```

#### Output:
```
[[]]
[["a"], ["b"], ["c"]]
[["a", "b"], ["a", "c"], ["b", "c"]]
[["a", "b", "c"]]
```
