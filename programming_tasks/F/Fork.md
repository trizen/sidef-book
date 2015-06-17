[1]: http://rosettacode.org/wiki/Fork

# [Fork][1]

```ruby
var x = 42;
var child = { x += 1 }.fork;
say child.wait; # prints: 43
say x;          # but x is still 42
```