[1]: https://rosettacode.org/wiki/Exactly_three_adjacent_3_in_lists

# [Exactly three adjacent 3 in lists][1]

```ruby
func contains_n_consecutive_objs(arr, n, obj) {
 
    # In Sidef >= 3.99, we can also say:
    # arr.contains(n.of(obj)...)
 
    arr.each_cons(n, {|*a|
        if (a.all { _ == obj }) {
            return true
        }
    })
 
    return false
}
 
var lists = [
    [9,3,3,3,2,1,7,8,5],
    [5,2,9,3,3,7,8,4,1],
    [1,4,3,6,7,3,8,3,2],
    [1,2,3,4,5,6,7,8,9],
    [4,6,8,7,2,3,3,3,1],
]
 
lists.each {|list|
    say (list, " => ", contains_n_consecutive_objs(list, 3, 3))
}
```

#### Output:
```
[9, 3, 3, 3, 2, 1, 7, 8, 5] => true
[5, 2, 9, 3, 3, 7, 8, 4, 1] => false
[1, 4, 3, 6, 7, 3, 8, 3, 2] => false
[1, 2, 3, 4, 5, 6, 7, 8, 9] => false
[4, 6, 8, 7, 2, 3, 3, 3, 1] => true
```
