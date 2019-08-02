[1]: https://rosettacode.org/wiki/Van_Eck_sequence

# [Van Eck sequence][1]

```ruby
func van_eck(n) {
 
    var seen = Hash()
    var seq  = [0]
    var prev = seq[-1]
 
    for k in (1 ..^ n) {
        seq << (seen.has(prev) ? (k - seen{prev}) : 0)
        seen{prev} = k
        prev = seq[-1]
    }
 
    seq
}
 
say van_eck(10)
say van_eck(1000).slice(991-1, 1000-1)
```

#### Output:
```
[0, 0, 1, 0, 2, 0, 2, 2, 1, 6]
[4, 7, 30, 25, 67, 225, 488, 0, 10, 136]
```
