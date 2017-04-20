[1]: http://rosettacode.org/wiki/Classes

# [Classes][1]

```ruby
class MyClass(instance_var) {
    method add(num) {
        instance_var += num
    }
}
 
var obj = MyClass(3)    # `instance_var` will be set to 3
obj.add(5)              # calls the add() method
say obj.instance_var    # prints the value of `instance_var`: 8
```
