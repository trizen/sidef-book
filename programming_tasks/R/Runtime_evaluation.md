[1]: https://rosettacode.org/wiki/Runtime_evaluation

# [Runtime evaluation][1]

The eval method evaluates a string as code and returns the resulting object.

```ruby
var (a, b) = (-5, 7)
say eval 'abs(a * b)'   # => 35
say abs(a * b)          # => 35
```
