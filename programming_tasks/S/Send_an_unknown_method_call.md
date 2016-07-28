[1]: http://rosettacode.org/wiki/Send_an_unknown_method_call

# [Send an unknown method call][1]

```ruby
class Example {
    method foo(x) {
        42 + x
    }
}

var name = 'foo'
var obj = Example()

say obj.(name)(5)          # prints: 47
say obj.method(name)(5)    # =//=
```
