[1]: https://rosettacode.org/wiki/Longest_common_subsequence

# [Longest common subsequence][1]

```ruby
func lcs(xstr, ystr) is cached {
 
    xstr.is_empty && return xstr
    ystr.is_empty && return ystr
 
    var(x, xs, y, ys) = (xstr.first(1), xstr.slice(1),
                         ystr.first(1), ystr.slice(1))
 
    if (x == y) {
        x + lcs(xs, ys)
    } else {
        [lcs(xstr, ys), lcs(xs, ystr)].max_by { .len }
    }
}
 
say lcs("thisisatest", "testing123testing")
```

#### Output:
```
tsitest
```
