[1]: https://rosettacode.org/wiki/Call_an_object_method

# [Call an object method][1]

```ruby
class MyClass {
    method foo(arg) { say arg }
}
 
var arg = 42
 
# Call a class method
MyClass.foo(arg)
 
# Alternatively, using an expression for the method name
MyClass.(:foo)(arg)
 
# Create an instance
var instance = MyClass()
 
# Instance method
instance.foo(arg)
 
# Alternatively, by using an expression for the method name
instance.(:foo)(arg)
 
# Alternatively, by asking for a method
instance.method(:foo)(arg)
```
