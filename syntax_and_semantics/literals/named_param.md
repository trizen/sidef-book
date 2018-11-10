# NamedParam

NamedParam is the type used to give named parameters to callables.

Its literal syntax uses the infix `:` operator, which may have an empty right-side, but whose left-side must not be a literal, and may be a name in the current scope.

```ruby
var a = "b"
"a": "b"                  # -> Pair("a", "b")
(a : "b")                 # -> Pair("b", "b")
a: "b"                    # -> NamedParam a: "b"

func foo(a, b = 2) { a/b }

var p = a: 4
say foo(p)                # -> 2

var args = [b:7, a:21]
say foo(args...)          # -> 3
```

It is not possible to write a function which takes a literal `NamedParam` argument, but this can be overcome by passing a variable reference that holds a `NamedParam` object, and later dereferencing it.

```ruby
func baz(param) {
  "Have #{param}, #{*param}"
}
var a = a:1
say baz(a)   # error: no matching function for parameter a
say baz(\a)  # prints: Have REF(0x55f9455ca270), a: 1
```
