[1]: https://rosettacode.org/wiki/First_missing_positive

# [First missing positive][1]

```ruby
func missing(a) {
    a = a.grep { .is_pos }.sort.uniq
    1..Inf -> first { |n| a.shift != n }
}
 
for a in ([
    [1,2,0], [3,4,-1,1], [7,8,9,11,12],
    [3,2,1,999999999999999999999999],
    [1,1,2,1,1], [-5,-4,-3]
]) {
    say "First missing positive for #{a} = #{missing(a)}"
}
```

#### Output:
```
First missing positive for [1, 2, 0] = 3
First missing positive for [3, 4, -1, 1] = 2
First missing positive for [7, 8, 9, 11, 12] = 1
First missing positive for [3, 2, 1, 999999999999999999999999] = 4
First missing positive for [1, 1, 2, 1, 1] = 3
First missing positive for [-5, -4, -3] = 1
```