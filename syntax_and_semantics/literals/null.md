# Null

The *Null* singleton type represents a defined value, with its specific meaning depending on the context in which it is used.

```ruby
null
defined(null)   # -> true
null.class      # -> Null
null.ref        # -> Sidef::Types::Null::Null
```

Unlike most Sidef typenames, it is not possible to refer to the Null type directly, because singleton classes have exactly one instance.
