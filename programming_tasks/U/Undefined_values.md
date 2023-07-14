[1]: https://rosettacode.org/wiki/Undefined_values

# [Undefined values][1]

Sidef variables are initialized with a default _nil_ value, representing the absence of a value.

```ruby
var x      # declared, but not defined
x == nil   && say "nil value"
defined(x) || say "undefined"
 
# Give "x" some value
x = 42
 
defined(x) && say "defined"
 
# Change "x" back to `nil`
x = nil
 
defined(x) || say "undefined"
```

#### Output:
```
nil value
undefined
defined
undefined
```
