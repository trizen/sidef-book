# try/catch

A `try/catch` construct it's used to try an unsafe block of code and catch any unexpected errors.

```ruby
var value = try   { isqrt(1764) }
            catch { die "error" }
say value   #=> 42
```

The `catch` branch is called only in case of a fatal error or when a `die` statement is executed in the `try` branch:

```ruby
var value = try {
    "foo".some_undefined_method
} catch { |msg|
    say "Catched: #{msg}"
    42
}
say value     #=> 42
```

The `try/catch` construct returns the result of the last statement from the first successfully executed branch.
