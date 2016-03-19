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
```
