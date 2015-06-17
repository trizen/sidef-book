[1]: http://rosettacode.org/wiki/Largest_int_from_concatenated_ints

# [Largest int from concatenated ints][1]

```ruby
func maxnum(nums) {
    nums.sort {|x,y|  "#{y}#{x}" <=> "#{x}#{y}" };
}
 
[[54, 546, 548, 60], [1, 34, 3, 98, 9, 76, 45, 4]].each { |c|
    say maxnum(c).join.to_num;
}
```

#### Output:
```
6054854654
998764543431
```