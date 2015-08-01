# Method precedence

Method precedence is controlled by the following three method separators: `.`, `->` and ` ` (space).

```ruby
1 + 25.sqrt;     # means: 1 + sqrt(25)
1 + 25->sqrt;    # means: (1+25).sqrt
1 + 25 sqrt;     # means: sqrt(1+25)
```

The rules are the following:

- `.` binds the method to the object which precedes the dot
- `->` makes everything from its left-side an expression and applies the method on the result
- `` `` applies the method linearly to whatever is on its left-side (almost identical with `->`)
