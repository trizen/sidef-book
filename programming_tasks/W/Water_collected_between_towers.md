[1]: https://rosettacode.org/wiki/Water_collected_between_towers

# [Water collected between towers][1]

```ruby
func max_l(Array a, m = a[0]) {
    gather { a.each {|e| take(m = max(m, e)) } }
}
 
func max_r(Array a) {
    max_l(a.flip).flip
}
 
func water_collected(Array towers) {
    var levels = (max_l(towers) »min« max_r(towers))
    (levels »-« towers).grep{ _ > 0 }.sum
}
 
[
    [ 1, 5,  3, 7, 2 ],
    [ 5, 3,  7, 2, 6, 4, 5, 9, 1, 2 ],
    [ 2, 6,  3, 5, 2, 8, 1, 4, 2, 2, 5, 3, 5, 7, 4, 1 ],
    [ 5, 5,  5, 5 ],
    [ 5, 6,  7, 8 ],
    [ 8, 7,  7, 6 ],
    [ 6, 7, 10, 7, 6 ],
].map { water_collected(_) }.say
```

#### Output:
```
[2, 14, 35, 0, 0, 0, 0]
```