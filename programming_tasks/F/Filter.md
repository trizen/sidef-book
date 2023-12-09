[1]: https://rosettacode.org/wiki/Filter

# [Filter][1]

```ruby
var arr = [1,2,3,4,5]

# Creates a new array
var new = arr.grep {|i| i.is_even }
say new    # => [2, 4]

# Destructive (at variable level)
arr.grep! {|i| i.is_even }
say arr    # => [2, 4]
```
