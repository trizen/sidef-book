[1]: http://rosettacode.org/wiki/Filter

# [Filter][1]

```ruby
var arr = [1,2,3,4,5];
 
# Creates a new array
var new = arr.grep { .is_even };
say new.dump;     # => [2, 4]
 
# Destructive (at variable level)
arr.grep! { .is_even };
say arr.dump;    # => [2, 4]
```
