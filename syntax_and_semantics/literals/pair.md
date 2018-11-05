# Pair

A Pair is a container for exactly two objects. Since Sidef is dynamically typed, its elements may be any type, including other Pairs.

This eliminates the need for a separate LinkedList class, as nested Pairs serve the same purpose.

If a Pair is created missing one or both elements, that element will be `nil`.

The literal syntax for creating Pairs is the [`:` method on Objects][pair_lit], which is not an operator, and therefore cannot have a `nil` left-side.

```ruby
"paired":"strings"        # -> Pair("paired", "strings")
Pair("paired", "strings") # -> ==/==

"a":nil                   # -> Pair("a", nil)
nil:"b"                   # -> error, methods cannot be called on undefined values
Pair(nil, "b")            # -> Pair(nil, "b")
```
Note that the Pair literal syntax does not round-trip, i.e `Pair.to_s` will never give the `:` representation.

When using the Pair literal syntax with variable names, this overlaps with the syntax for Complex numbers and NamedParams.

```ruby
var (a, b) = ("a", "b")
say a:b                 # prints "a:"
say a:b.is_a(Pair)      # prints false
say a:b.class           # prints NamedParam
var (c, d) = (1, 2)     
say c:d                 # prints 1+2i
say c:d.is_a(Pair)      # prints false
say c:d.class           # prints Complex
```
When the left-hand side is not a number, force evaluation of `:` as a method with `.` or `\`:

```ruby
say a.:b                # prints Pair("a", "b")
say a\:b                # ==/==
say (a : b)             # ==/==
say Pair(a, b)          # ==/==

say c.:d                # prints 1+2i
say c\:d                # ==/==
say (c : d)             # ==/==
say Pair(c, d)          # prints Pair(1, 2)
```

Note this does not override the Complex literal when the left-hand side *is* a number.

## Indexing

Pair objects can be indexed directly, but also define the `first` / `key` and `second` / `value` methods:

```ruby
var pair = Pair(1, 2)
say pair.first        # prints 1
say pair.key          # ==/==
say pair[0]           # ==/==
say pair.second       # prints 2
say pair.value        # ==/==
say pair[1]           # ==/==

say pair[2]           # prints nil
say pair[4..10]       # a range of nils
```

Like other iterable and indexable objects, accessing a nonexistent Pair element gives `nil`.

# Nesting

To use nested pairs like a Lisp-style linked list, the `second` or `value` methods can be chained, as long as the second element is always a Pair.

The *`:` method* can be combined with the *infix `:` operator*, which symbol-ifies its operand, to easily write chains and linked lists of Strings.

```ruby
:a                                # -> "a", the named variable a
:a: :chain: :of: :string: :pairs  # -> Pair("a", Pair("chain", Pair("of", Pair("string", "pairs"))))
:a::chain::of::string::pairs      # -> ==/==
:a::chain::of::string::pairs:     # -> Pair(String, NamedParam)
```
Including a trailing `:` in such chains will cause the rest of the expression to be parsed as a `NamedParam`.

To make this a (old-style) linked list, we should be able to find the end, thus include a trailing `nil` (or `null`, or `false`...). Then we can traverse it, destructively for brevity:

```ruby
var list = :a: :linked: :list: :of: :pairs: :of: :strings: nil

var copy = list.dclone

# imperative style
loop {
  print copy.key+" "
  break if (! copy.value!)
}

# prints: a linked list of pairs of strings
# copy is now nil, the terminating element

# functional style
func traverse (list) {
  print list.key+" "
  __FUNC__(list) if list.value!
}

traverse(list.dclone)

# prints: a linked list of pairs of strings
```

The `swap` method can be used to transpose the first and second elements:

```ruby
(:a : :b)       # -> Pair("a", "b")
(:a : :b).swap  # -> Pair("b", "a")
```

[pair_lit]: https://github.com/trizen/sidef/commit/2f33be54ff6eb15533d20f39c093fec2503362b6
