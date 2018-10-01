# Set

A set is an ordered collection of objects, with no duplicates.

```ruby
Set('foo', 'bar', 'baz')
```

## Operations

All the set operators, such as intersection, difference, symmetric difference, union and concatenation, are supported.

```ruby
var A = Set('foo', 'bar', 'baz', 'foo')
var B = Set('bar', 'foo', 'qux')

# Intersection
say (A & B)         #=> Set("foo", "bar")

# Union
say (A | B)         #=> Set("foo", "qux", "bar", "baz")

# Difference
say (A - B)         #=> Set("baz")
say (B - A)         #=> Set("qux")

# Symmetric difference
say (A ^ B)         #=> Set("baz", "qux")

# Concatenation
say (A + B)         #=> Set("baz", "bar", "qux", "foo")
```

## Updating

The method `set.delete(obj)` can be used for removing a given object from the set.
