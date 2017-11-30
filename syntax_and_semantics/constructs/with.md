# with

The `with` statement behaves almost like the `if` statement, but instead of testing for trueness, it checks to see if the given argument is not a `nil` value.

```ruby
with (obj) {

}
orwith (obj) {

}
else {

}
```

Same as the `if` statement, it supports capturing of a defined value in a block variable:

```ruby
with (some_function()) { |value|
    say value
}
```
