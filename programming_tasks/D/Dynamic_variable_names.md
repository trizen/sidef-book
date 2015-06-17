[1]: http://rosettacode.org/wiki/Dynamic_variable_names

# [Dynamic variable names][1]

It is not possible to create a new lexical variable at run-time, but there are other various ways to do something similar.

```ruby
var name = Sys.scanln("Enter a variable name: ");   # type in 'foo'
struct _{};
.(name) = 42;
say .foo;     # prints: 42
```