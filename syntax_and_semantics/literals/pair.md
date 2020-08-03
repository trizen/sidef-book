# Pair

The Pair class represents a 2-element array.

```ruby
var p = Pair(42, 99)

say p.first      #=> 42
say p.second     #=> 99

p.first = "foo"     # change first element
p.second = "bar"    # change second element

say p       #=> Pair("foo", "bar")
```

Linked lists can be created using nested Pair objects:

```ruby
var ll = Pair(1, Pair(2, Pair(3, 4)))

loop {
    say ll.first
    if (ll.second.kind_of(Pair)) {
        ll = ll.second
    }
    else {
        say "Reached end: #{ll.second}"
        break
    }
}
```
