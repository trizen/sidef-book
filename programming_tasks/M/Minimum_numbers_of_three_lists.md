[1]: https://rosettacode.org/wiki/Minimum_numbers_of_three_lists

# [Minimum numbers of three lists][1]

```ruby
var lists = [
    [ 5, 45, 23, 21, 67],
    [43, 22, 78, 46, 38],
    [ 9, 98, 12, 98, 53],
]
 
say lists.zip.map{.min}
```

#### Output:
```
[5, 22, 12, 21, 38]
```
