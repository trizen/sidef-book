# Methods

A method is a distinct function defined for a specific type of object. There may be methods that share the same name, but each pointing at different functions, depending on the type of the object on which they are invoked.

```ruby
"string".length     # String.length()
[1,2,3].length      # Array.length()
```

The methods can also be invoked using the prefix notation:

```ruby
length("string")
length([1,2,3])
```

The prefix and postfix notations can be used interchangeably:

```ruby
log("string".length)    # means: "string".length.log
length("string").log    # =//=
log(length("string"))   # =//=
```

Starting with Sidef 2.30, a method can be invoked, using the prefix notation, even when a function with the same name is declared in the same scope:

```ruby
func sqrt(n) { "sqrt of #{n} is #{n.sqrt}" }

say   sqrt(42)     # calls the `sqrt` function defined above
say ::sqrt(42)     # calls the `Number.sqrt()` method
```

Additionally, any alphanumeric method name can be used as an infix operator, by surrounding it with two backticks:

```ruby
(1 `add` 2)           # means: 1.add(2)
(Math `sum` (1,2,3))  # means: Math.sum(1,2,3)
```

There is also support for calling a method which its name is not known until at run-time, which can be any expression that evaluates to a string:

```ruby
say ( 50.(['+', '-'].rand)(30) )    # prints 20 or 80
```

If a method is not found for a given object, Sidef will throw a run-time error.
