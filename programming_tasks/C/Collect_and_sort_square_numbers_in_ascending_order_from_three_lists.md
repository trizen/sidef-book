[1]: https://rosettacode.org/wiki/Collect_and_sort_square_numbers_in_ascending_order_from_three_lists

# [Collect and sort square numbers in ascending order from three lists][1]

```ruby
var lists = [
  [3,4,34,25,9,12,36,56,36],
  [2,8,81,169,34,55,76,49,7],
  [75,121,75,144,35,16,46,35],
]
 
say lists.flat.grep{.is_square}.sort
```

#### Output:
```
[4, 9, 16, 25, 36, 36, 49, 81, 121, 144, 169]
```
