[1]: http://rosettacode.org/wiki/Call_an_object_method

# [Call an object method][1]

```ruby
class MyClass {
    method foo(arg) { say arg }
}
 
var arg = 42;
 
# Class method
MyClass.method(:foo)(arg);
 
# Alternatively, by specifying the self-object
MyClass.invoke(:foo, MyClass, arg);
 
# Create an instance
var instance = MyClass();
 
# Instance method
instance.foo(arg);
 
# Alternatively, by using an expression as a method
instance.(:foo)(arg);
 
# Alternatively, by asking for a method
instance.method(:foo)(arg);
```