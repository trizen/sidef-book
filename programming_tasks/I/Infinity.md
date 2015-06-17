[1]: http://rosettacode.org/wiki/Infinity

# [Infinity][1]

```ruby
var a = 1.5/0;        # inf
say a.is_inf;         # true
say a.is_pos;         # true
 
var b = -1.5/0;       # -inf
say b.is_inf;         # true
say b.is_neg;         # true
 
var inf = Math.inf;
var ninf = -Math.inf;
say (inf == -ninf);   # true
```