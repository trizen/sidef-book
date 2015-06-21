# Array

An Array is a collection of objects which can grow or shrink dynamically.

```ruby
[123, "abc", true, nil]
```

## Special arrays

Arrays of strings or numbers can be created with a special syntax:

```ruby
%w(1 two three)         # same as: ["1", "two", "three"]
%n(1 2.5 3.75)          # same as: [1, 2.5, 3.75]
%i(1 2.5 3.75)          # same as: [1, 2, 3]
```

Unescaped spaces and unescaped comments are removed from the declaration For example, the following declaration:

```ruby
%w(
    Sidney        # Australia
    New\ York     # U.S.A
)
```

...is equivalent with `["Sidney", "New York"]`.


There is also `%W(...)` which understands escapes and interpolation:

```ruby
%W(
    hello\tworld
    one\ word         # some comment
    \#{1+2}
)
```

...which means: `["hello\tworld", "one word", "3"]`.


Another way is by using the `<...>` and `«...»` delimiters, which will try to determine the types automatically for you:

```ruby
<I 8 some 3.14>         # same as: ["I", 8, "some", 3.14]
```
