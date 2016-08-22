# Method precedence

Method precedence is controlled by the following two method separators: `.` and `->`.

```ruby
1 + 25.sqrt      # means: 1 + sqrt(25)
1 + 25->sqrt     # means: sqrt(1 + 25)
```

The rules are the following:

- `.` binds the method to the object which precedes the dot
- `->` makes everything from its left-side an expression and applies the method on the result

The infix backslash (`\`) removes any leading or trailing whitespace at that current position and it's useful for expanding method calls on multiple lines:

```ruby
say "abc".uc      \
         .reverse \
         .chars
```

is equivalent with:

```ruby
say "abc".uc.reverse.chars
```
