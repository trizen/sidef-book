# Methods

Everything in Sidef is an object which responds to methods. A method is a distinct function defined for a specific type of object.

There may be methods that share the same name, but each pointing at different functions, depending on the type of the object on which they are applied.

```ruby
"string".length;    # String.length()
[1,2,3].length;     # Array.length()
```

The methods can also be called, using the prefix notation:

```ruby
length("string");
length([1,2,3]);
```

The parentheses are optional when the method is called with only one argument.

```ruby
int 12.5;   # means: int(12.5) which means: 12.5.int
```

The prefix and postfix notations can be combined:

```ruby
say "string".length;    # means: "string".length.say
length("string").say;   # =//=
```
