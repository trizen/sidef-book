[1]: http://rosettacode.org/wiki/Copy_a_string

# [Copy a string][1]

```ruby
var original = "hello";               # new String object
var reference = original;             # points at the original object
var copy1 = String.new(original);     # creates a new String object
var copy2 = original+'';              # ==//==
```