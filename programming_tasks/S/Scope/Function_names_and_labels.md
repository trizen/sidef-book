[1]: http://rosettacode.org/wiki/Scope/Function_names_and_labels

# [Scope/Function names and labels][1]

In Sidef, the same rule which is applied to variable scoping, is applied to functions and classes as well, which means that a function defined inside another function is not visible outside the current scope.

```ruby
# Nested functions
func outer {
    func inner {};   # not visible outside
}
 
# Nested classes
class Outer {
    class Inner {};  # not visisble outside
}
```