[1]: https://rosettacode.org/wiki/Centroid_of_a_set_of_N-dimensional_points

# [Centroid of a set of N-dimensional points][1]

```ruby
func centroid(l) {
    l.combine {|*a| a.sum } »/» l.len
}

[
    [ [1], [2], [3] ],
    [ [8, 2], [0, 0] ],
    [ [5, 5, 0], [10, 10, 0] ],
    [ [1, 3.1, 6.5], [-2, -5, 3.4], [-7, -4, 9], [2, 0, 3] ],
    [ [0, 0, 0, 0, 1], [0, 0, 0, 1, 0], [0, 0, 1, 0, 0], [0, 1, 0, 0, 0] ],
].each {
    say centroid(_)
}
```

#### Output:
```
[2]
[4, 1]
[15/2, 15/2, 0]
[-3/2, -59/40, 219/40]
[0, 1/4, 1/4, 1/4, 1/4]
```
