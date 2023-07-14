[1]: https://rosettacode.org/wiki/Add_a_variable_to_a_class_instance_at_runtime

# [Add a variable to a class instance at runtime][1]

```ruby
class Empty{};
var e = Empty();    # create a new class instance
e{:foo} = 42;       # add variable 'foo'
say e{:foo};        # print the value of 'foo'
```