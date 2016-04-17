# Types

A function can be declared with typed parameters, which are checked at run-time.

```ruby
func concat(String a, String b) {
    a + b
}
```

Now, the function can only be called with strings as arguments:

```ruby
say concat("o", "k")  # ok
say concat(1, 2)      # run-time error
```

The typed parameters require a specific type of object, but they do not default to anything when no value is provided. This means that all typed-parameters are mandatory, unless a default value is provided:

```ruby
func concat(String a="foo", String b="bar") {
   a + b
}

say concat()          # prints: "foobar"
say concat("mini")    # prints: "minibar"
say concat(1, 2)      # this is still a run-time error
```

An user-defined type is just a class:

```ruby
class Point(Number x, Number y) {
    method to_s { "Point(#{x}, #{y})" }      # auto-stringification
}

func foo(Point p) {
    say p
}

foo(Point(5, 6))
```
