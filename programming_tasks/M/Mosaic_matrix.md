[1]: https://rosettacode.org/wiki/Mosaic_matrix

# [Mosaic matrix][1]

```ruby
func mosaic_matrix(n) {
    n.of {|k|
        var(a,b) = (k.is_even ? (1,0) : (0,1))
        n.of {|j| j.is_even ? a : b }
    }
}
 
mosaic_matrix(5).each { .join(' ').say }; say ''
mosaic_matrix(6).each { .join(' ').say }
```

#### Output:
```
1 0 1 0 1
0 1 0 1 0
1 0 1 0 1
0 1 0 1 0
1 0 1 0 1

1 0 1 0 1 0
0 1 0 1 0 1
1 0 1 0 1 0
0 1 0 1 0 1
1 0 1 0 1 0
0 1 0 1 0 1
```
