[1]: http://rosettacode.org/wiki/Return_multiple_values

# [Return multiple values][1]

The _return_ keyword can return multiple values from functions. In its absence, only one value is returned.

```ruby
func foo(a,b) {
    return (a+b, a*b);
};
```
```ruby
var (x, y) = foo(4, 5);
```