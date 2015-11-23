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

Where `type` is either `error` or `warning`.
