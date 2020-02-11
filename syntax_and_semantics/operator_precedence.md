# Operator precedence

All operators have the same precedence, which is controlled by the lack of whitespace between the operands.

```ruby
1+2 * 3+4   # means: (1+2) * (3+4)
```

In the above example, the lack of whitespace between `1`, `+` and `2`, classifies the operation as a distinct expression.

The implications are the following:

```ruby
var n = 1 + 2       # incorrect -- it means: (var n = 1) + 2
var n = 1+2         # correct
var n = (1 + 2)     # correct
```

When no precedence is defined, the order of operations is from left to right:

```ruby
1 + 2 * 3       # means: ((1 + 2) * 3)
```

On the other hand, when too much precedence is defined, the order is from right to left:

```ruby
1+2*3           # means: (1 + (2 * 3))
```

The precedence can also be controlled by backslashing or preceding the operator with a dot.

```ruby
1 + 2 \* 3      # means: (1 + (2 * 3))
1 + 2 .* 3      # =//=
```
