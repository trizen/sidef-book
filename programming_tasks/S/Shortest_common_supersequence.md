[1]: https://rosettacode.org/wiki/Shortest_common_supersequence

# [Shortest common supersequence][1]

Uses the *lcs* function defined [here](https://rosettacode.org/wiki/Longest_common_subsequence#Sidef).

```ruby
func scs(u, v) {
    var ls = lcs(u, v).chars
    var pat = Regex('(.*)'+ls.join('(.*)')+'(.*)')
    u.scan!(pat)
    v.scan!(pat)
    var ss = (u.shift + v.shift)
    ls.each { |c| ss += (c + u.shift + v.shift) }
    return ss
}
 
say scs("abcbdab", "bdcaba")
```

#### Output:
```
abdcabdab
```