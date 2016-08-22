# Lazy methods

Lazy methods provide an interesting concept of partially applying a method on a given object, delaying the evaluation until the result is needed.

```ruby
var lz = 42.method('>')        #=> LazyMethod
say lz(41)                     #=> true (i.e.: 42 > 41)
```

`Object.method()` returns a `LazyMethod` object which can be called just like any other function, producing the result by calling the method which is stored inside the `LazyMethod` object.

This allow us to store or pass around partial expressions, which can be evaluated multiple times at any point in the future:

```ruby
var str = "a-b-c"
var lzsplit = str.method(:uc).method(:split)

say lzsplit('')         #=> ["A", "-", "B", "-", "C"]
say lzsplit('-')        #=> ["A", "B", "C"]
```
