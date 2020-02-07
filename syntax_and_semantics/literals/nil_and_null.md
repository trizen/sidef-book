# Nil and Null

## Nil

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

## Null

The *Null* singleton type represents a defined value, with its specific meaning depending on the context in which it is used.

```ruby
null
defined(null)   # -> true
null.class      # -> Null
null.ref        # -> Sidef::Types::Null::Null
```

Unlike most Sidef typenames, it is not possible to refer to the Null type directly, because singleton classes have exactly one instance.
