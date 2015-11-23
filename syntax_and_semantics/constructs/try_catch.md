# try/catch

A `try/catch` construct it's used to try an unsafe block of code and catch any unexpected errors.

```ruby
try {
    "string".some_undefined_method
}
catch { |type, msg|
    say "Catched the following #{type}: #{msg}"
}
```

#### Output:

```
Catched the following error: Undefined method: Sidef::Types::String::String::some_undefined_method at /Sidef/lib/Sidef.pm line 57.
```
