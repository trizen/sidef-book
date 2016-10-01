[1]: http://rosettacode.org/wiki/Levenshtein_distance

# [Levenshtein distance][1]

Recursive:

```ruby
func lev(s, t) is cached {
 
    s.is_empty && return t.len;
    t.is_empty && return s.len;
 
    var s1 = s.ft(1);
    var t1 = t.ft(1);
 
    s[0] == t[0] ? __FUNC__(s1, t1)
                 : 1+[
                        __FUNC__(s1, t1),
                        __FUNC__(s,  t1),
                        __FUNC__(s1, t )
                     ].min;
}
```

Iterative:

```ruby
func lev(s, t) {
    var d = [@(0 .. t.len), s.len.of {[_]}...]
    for i,j in (^s ~X ^t) {
        d[i+1][j+1] = (
            s[i] == t[j]
                ? d[i][j]
                : 1+Math.min(d[i][j+1], d[i+1][j], d[i][j])
        )
    }
    d[-1][-1]
}
```


Calling the function:

```ruby
say lev(%c'kitten', %c'sitting');               # prints: 3
say lev(%c'rosettacode', %c'raisethysword');    # prints: 8
```
