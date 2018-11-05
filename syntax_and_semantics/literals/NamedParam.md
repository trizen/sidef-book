# NamedParam

NamedParam is the type used to give named parameters to callables.

Its literal syntax uses the infix `:` operator, which may have an empty right-side, but whose left-side must not be a literal, and may be a name in the current scope.

```ruby
var a = "b"
"a": "b"                  # -> Pair("a", "b")
(a : "b")                 # -> Pair("b", "b")
a: "b"                    # -> NamedParam a: "b"

func foo(a, b) { a/b }
var args = [b:7, a:21]
say foo(args...)          # -> 3
```
