[1]: http://rosettacode.org/wiki/Runtime_evaluation

# [Runtime evaluation][1]

The eval method evaluates a string as code and returns the resulting object.

```ruby
var (a, b) = (-5, 7);
say eval '(a * b).abs';  # => 35
say (a * b -> abs);      # => 35
```