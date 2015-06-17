[1]: http://rosettacode.org/wiki/Longest_common_subsequence

# [Longest common subsequence][1]

```ruby
func lcs(xstr is String, ystr is String) -> String {
    (xstr.is_empty || ystr.is_empty) && return '';
 
    var(x, xs, y, ys) = (xstr.ft(0, 1), xstr.ft(1),
                         ystr.ft(0, 1), ystr.ft(1));
 
    if (x == y) {
        x + lcs($xs, $ys)
    } else {
        [lcs(xstr, ys), lcs(xs, ystr)].max_by {|x| x.len};
    }
}
 
say lcs("thisisatest", "testing123testing");
```

#### Output:
```
% time sidef -Mblock lcs.sf
tsitest
sidef -Mblock lcs.sf  0.23s user 0.01s system 97% cpu 0.240 total
```