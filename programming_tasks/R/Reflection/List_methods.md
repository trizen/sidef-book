[1]: https://rosettacode.org/wiki/Reflection/List_methods

# [Reflection/List methods][1]

The super-method *Object.methods()* returns an Hash with method names as keys and *LazyMethod* objects as values. Each *LazyMethod* can be called with zero or more arguments, internally invoking the method on the object on which *.methods* was called.

```ruby
class Example {
    method foo { }
    method bar(arg) { say "bar(#{arg})" }
}
 
var obj = Example()
say obj.methods.keys.sort          #=> ["bar", "call", "foo", "new"]
 
var meth = obj.methods.item(:bar)  # `LazyMethod` representation for `obj.bar()`
meth(123)                          # calls obj.bar()
```