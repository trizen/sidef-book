# try/catch

A `try/catch` construct it's used to try an unsafe block of code and catch any unexpected errors.

```ruby
try {
    "foo".some_undefined_method
}
catch { |type, msg|
    say "Catched the following #{type}: #{msg}"
}
```

#### Output:

```
Catched the following error: Undefined method `String.some_undefined_method' called from ...
```
