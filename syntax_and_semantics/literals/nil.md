# Nil

The `nil` type represents the absence of a value, and is considered undefined:

```ruby
nil
defined(nil)  # -> false
nil.class     # -> error, methods cannot be called on undefined values
nil.ref       # -> error, methods cannot be called on undefined values
```

The `nil` type has only one possible representation, `nil`.

Instead of an error or exception, an *undefined* value is represented by `nil`:

```ruby
Hash(){:key}    # -> nil
```
