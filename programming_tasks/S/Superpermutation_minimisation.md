[1]: http://rosettacode.org/wiki/Superpermutation_minimisation

# [Superpermutation minimisation][1]

```ruby
1..8 -> each { |len|
    var (pre="", post="")
    ^len -> to_a.permutations {|p|
        var t = p.join
        post.append!(t) if !post.contains(t)
        pre.prepend!(t) if !pre.contains(t)
    }
    printf("%2d: %8d %8d\n", len, pre.len, post.len)
}
```

#### Output:
```
 1:        1        1
 2:        4        4
 3:       12       15
 4:       48       64
 5:      240      325
 6:     1440     1956
 7:    10080    13699
 8:    80640   109600
```