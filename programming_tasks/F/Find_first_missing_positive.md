[1]: https://rosettacode.org/wiki/Find_first_missing_positive

# [Find first missing positive][1]

```ruby
[[1,2,0], [3,4,1,1], [7,8,9,11,12],[1,2,3,4,5],
[-6,-5,-2,-1], [5,-5], [-2], [1], []].each {|arr|
    var s = Set(arr...)
    say (arr, " ==> ", 1..Inf -> first {|k| !s.has(k) })
}
```

#### Output:
```
[1, 2, 0] ==> 3
[3, 4, 1, 1] ==> 2
[7, 8, 9, 11, 12] ==> 1
[1, 2, 3, 4, 5] ==> 6
[-6, -5, -2, -1] ==> 1
[5, -5] ==> 1
[-2] ==> 1
[1] ==> 2
[] ==> 1
```
