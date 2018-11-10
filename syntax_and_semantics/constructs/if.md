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

Because Sidef is weakly typed, the condition inside the `if` statement can be any object, which is implicitly converted to a `Bool` object. However, the value stored inside the captured block variable will be the result of the original expression, which may not necessarily be a `Bool` object.

Note that the captured value won't have any other methods called on it before being captured, for example the following may be unexpected: 

```ruby
var str = "ab"
if (str =~ /^a(.)$/) { |m|
    say m
    say m=="b"
    say m.class
    say m.dump
}
```

It will output

```ruby
b
false
Match
(str =~ /^a(.)$/) # a Match object
```

because the entire Match object from the match expression `=~` will be captured by the Block. To save the first capture and make `m=="b"`, use `(str=~/^a(.)$/)[0]`.
