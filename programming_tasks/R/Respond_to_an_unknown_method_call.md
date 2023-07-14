[1]: https://rosettacode.org/wiki/Respond_to_an_unknown_method_call

# [Respond to an unknown method call][1]

The special *AUTOLOAD* method gets called when a method isn't defined in the current class:

```ruby
class Example {
    method foo {
        say "this is foo"
    }
    method bar {
        say "this is bar"
    }
    method AUTOLOAD(_, name, *args) {
        say ("tried to handle unknown method %s" % name)
        if (args.len > 0) {
            say ("it had arguments: %s" % args.join(', '))
        }
    }
}
 
var example = Example.new
 
example.foo           # prints “this is foo”
example.bar           # prints “this is bar”
example.grill         # prints “tried to handle unknown method grill”
example.ding("dong")  # prints “tried to handle unknown method ding”
                      # prints “it had arguments: dong”
```
