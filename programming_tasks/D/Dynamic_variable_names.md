[1]: https://rosettacode.org/wiki/Dynamic_variable_names

# [Dynamic variable names][1]

It is not possible to create a new lexical variable at run-time, but there are other various ways to do something similar.

```ruby
var name = read("Enter a variable name: ", String);     # type in 'foo'

class DynamicVar(name, value) {
    method init {
        DynamicVar.def_method(name, ->(_) { value })
    }
}

var v = DynamicVar(name, 42);       # creates a dynamic variable
say v.foo;                          # retrieves the value
```
