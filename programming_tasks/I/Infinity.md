[1]: http://rosettacode.org/wiki/Infinity

# [Infinity][1]

```ruby
var a = 1.5/0        # Inf
say a.is_inf         # true
say a.is_pos         # true
 
var b = -1.5/0       # -Inf
say b.is_ninf        # true
say b.is_neg         # true

var inf = Inf
var ninf = -Inf
say (inf == -ninf)   # true
```
