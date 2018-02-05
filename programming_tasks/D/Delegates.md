[1]: https://rosettacode.org/wiki/Delegates

# [Delegates][1]

```ruby
class NonDelegate { }
 
class Delegate {
    method thing {
        return "delegate implementation"
    }
}
 
class Delegator (delegate = null) {
    method operation {
 
        if (delegate.respond_to(:thing)) {
            return delegate.thing
        }
 
        return "default implementation"
    }
}
 
var d = Delegator()
say "empty: #{d.operation}"
d.delegate = NonDelegate()
say "NonDelegate: #{d.operation}"
d.delegate = Delegate()
say "Delegate: #{d.operation}"
```

#### Output:
```
empty: default implementation
NonDelegate: default implementation
Delegate: delegate implementation
```