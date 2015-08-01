# Operator precedence

In Sidef, the operator precedence rules are fundamentally different from other languages.

All operators have the same precedence, which is controlled by the lack of whitespace between the operands.

```ruby
1+2 * 3+4   # means: (1+2) * (3+4)
```

In the above example, the lack of whitespace between `1`, `+` and `2`, classifies the operation as a distinct expression.

The implications are the following:

```ruby
var n = 1 + 2;      # wrong -- it means: (var n = 1) + 2
var n = 1+2;        # correct
var n = (1+2);      # correct
```
