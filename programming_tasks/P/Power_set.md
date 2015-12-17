[1]: http://rosettacode.org/wiki/Power_set

# [Power set][1]

```ruby
var arr = %w(a b c);
0.to(arr.len).each { |i|
    say arr.combinations(i);
}
```

#### Output:
```
[[]]
[["a"], ["b"], ["c"]]
[["a", "b"], ["a", "c"], ["b", "c"]]
[["a", "b", "c"]]
```
