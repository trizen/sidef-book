# if

The `if` statement is one of the most basic conditional constructs.

```ruby
var a = 21
var b = 42

if (a > b) {
    say "a is greater"
}
elsif (a == b) {
    say "a and b are equal"
}
else {
    say "b is greater"
}
```

A somewhat special feature is the support for capturing the original value evaluated in the `if` statement, such as:

```ruby
if (some_function()) { |value|
    say value
}
```

Because Sidef is weakly typed, the condition inside the `if` statement can be any object, which is implicitly converted to a `Bool` object. However, the value stored inside the captured block variable, will be the original value, which may not necessarily be a `Bool` object.
