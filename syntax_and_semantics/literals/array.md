# Array

An Array is a collection of objects which can grow or shrink dynamically.

```ruby
[123, "abc", true, nil]
```

Alternatively, one can write:

```ruby
Array(123, "abc", true, nil)
```

## Working with arrays:

Elements of an array can be accessed with the special syntax `array[i]` where `i` is a zero-based index inside the array.

```ruby
var array = [1, 2, 3, 4, 5]

array[0] = 6
array[1] = 7

say array
```

## Special arrays

Arrays of strings or numbers can be created with a special syntax:

```ruby
%w(1 two three)         # same as: ["1", "two", "three"]
%n(1 2.5 3.75)          # same as: [1, 2.5, 3.75]
%i(1 2.5 3.75)          # same as: [1, 2, 3]
```

Unescaped spaces and unescaped comments are removed. For example, the following declaration:

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
    one\ item         # some comment
    \#{1+2}
)
```

...which means: `["hello\tworld", "one item", "3"]`.


Another way is by using the `<...>` and `«...»` delimiters:

```ruby
<I 8 some 3.14>         # same as: ["I", "8", "some", "3.14"]
```
