[1]: https://rosettacode.org/wiki/Append_numbers_at_same_position_in_strings

# [Append numbers at same position in strings][1]

```ruby
var lists = [
    [1,2,3,4,5,6,7,8,9],
    [10,11,12,13,14,15,16,17,18],
    [19,20,21,22,23,24,25,26,27],
]
 
say lists.zip.map_2d {|*a| a.join.to_i }
```

#### Output:
```
[11019, 21120, 31221, 41322, 51423, 61524, 71625, 81726, 91827]
```
