[1]: http://rosettacode.org/wiki/Levenshtein_distance

# [Levenshtein distance][1]

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
```ruby
func lev(s, t) {
    var d = [ 0 .. t.len, 1 .. s.len -> map {[_]}...];
    { |i|
        { |j|
            d[i][j] = (
                    s[i-1] == t[j-1]
                ? d[i-1][j-1]
                : [d[i-1][j], d[i][j-1], d[i-1][j-1]].min+1;
              );
        } * t.len;
    } * s.len;
    d[-1][-1] \\ [s.len, t.len].min;
}
```


Calling the function:

```ruby
say lev(%c'kitten', %c'sitting');               # prints: 3
say lev(%c'rosettacode', %c'raisethysword');    # prints: 8
```