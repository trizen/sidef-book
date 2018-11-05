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

<!--
This, with the slurpy parameter `:hash`, allows for Python-style arbitrary keyword arguments:

```ruby
func bar(:kw_args) {
  say kw_args
}
bar(a: 1, a_random_arg: "ok") # prints:
```
-->
It would seem impossible to then write a function which takes a literal NamedParam argument, but this can be achieved by taking a reference to the parameter and later dereferencing.

```ruby
func baz(param) {
  "Have #{param}, #{*param}"
}
var a = a:1
say baz(a)   # -> error, no matching function for parameter a
say baz(\a)  # prints: Have REF(0x55f9455ca270), a: 1
```
