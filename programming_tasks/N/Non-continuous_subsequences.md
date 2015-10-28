[1]: http://rosettacode.org/wiki/Non-continuous_subsequences

# [Non-continuous subsequences][1]

```ruby
func non_continuous(min, max, subseq=[], has_gap=false) {
 
    static current = [];
 
    range(min, max).each { |i|
        current.push(i);
        has_gap && subseq.append([current...]);
        i < max && non_continuous(i.inc, max, subseq, has_gap);
        current.pop;
        has_gap = current.len;
    }
 
    subseq;
}
 
say non_continuous(1, 3);
say non_continuous(1, 4);
say non_continuous("a", "d");
```

#### Output:
```
[[1, 3]]
[[1, 2, 4], [1, 3], [1, 3, 4], [1, 4], [2, 4]]
[["a", "b", "d"], ["a", "c"], ["a", "c", "d"], ["a", "d"], ["b", "d"]]
```