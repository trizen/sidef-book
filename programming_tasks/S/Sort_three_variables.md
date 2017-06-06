[1]: https://rosettacode.org/wiki/Sort_three_variables

# [Sort three variables][1]

Generalized solution, for an arbitrary number of variable references:

```ruby
func sort_refs(*arr) {
    arr.map{ *_ }.sort ~Z arr -> each { *_[1] = _[0] }
}
 
var x = 77444
var y =   -12
var z =     0
 
sort_refs(\x, \y, \z)
 
say x
say y
say z
```

#### Output:
```
-12
0
77444
```


Alternatively, without using a sorting function:

```ruby
var x = 77444
var y =   -12
var z =     0
 
(x, y) = (y, x) if (x > y)
(x, z) = (z, x) if (x > z)
(y, z) = (z, y) if (y > z)
 
say x
say y
say z
```

#### Output:
```
-12
0
77444
```