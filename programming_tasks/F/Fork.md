[1]: https://rosettacode.org/wiki/Fork

# [Fork][1]

```ruby
var x = 42
{ x += 1; say x }.fork.wait      # x is 43 here
say x                            # but here is still 42
```
