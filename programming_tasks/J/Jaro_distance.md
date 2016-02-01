[1]: http://rosettacode.org/wiki/Jaro_distance

# [Jaro distance][1]

```ruby
func jaro(s, t) {
 
    var s_len = s.len
    var t_len = t.len
 
    var match_distance = (floor(max(s_len, t_len) / 2) - 1)
 
    var s_matches = []
    var t_matches = []
 
    var matches = 0
    var transpositions = 0
 
    s_len.range.each { |i|
        var start = max(0, i-match_distance)
        var end = min(i+match_distance, t_len-1)
 
        start ... end -> each { |k|
            t_matches[k] && next
            s[i] == t[k] || next
            s_matches[i] = true
            t_matches[k] = true
            matches++
            break
        }
    }
 
    return 0 if (matches == 0)
 
    var k = 0
    s_len.range.each { |i|
        s_matches[i] || next
        while (!t_matches[k]) { ++k }
        s[i] == t[k] || ++transpositions
        ++k
    }
 
    ((matches / s_len) +
      (matches / t_len) +
        ((matches - transpositions/2) / matches)) / 3
}
 
for pair in [
    [%c"MARTHA",    %c"MARHTA"],
    [%c"DIXON",     %c"DICKSONX"],
    [%c"JELLYFISH", %c"SMELLYFISH"],
] {
    say "jaro(#{pair.map{.join.dump}.join(', ')}) = #{'%.10f' % jaro(pair...)}"
}
```

#### Output:
```
jaro("MARTHA", "MARHTA") = 0.9444444444
jaro("DIXON", "DICKSONX") = 0.7666666667
jaro("JELLYFISH", "SMELLYFISH") = 0.8962962963
```