# Bag

A bag (also known as a multi-set) is a unordered collection of objects, similar to a hash table, where each object has a count number, which represents the number of times it exists in the bag.

```ruby
Bag('foo', 'bar', 'baz')
```

## Operations

The Bag class supports all the set operators, such as intersection, difference, symmetric difference, union and concatenation.

```ruby
var A = Bag('foo', 'bar', 'baz', 'foo')
var B = Bag('bar', 'foo', 'qux')

# Count how many times is 'foo' present in the bag A
say A.count('foo')  #=> 2

# Intersection
say (A & B)         #=> Bag("foo", "bar")

# Union
say (A | B)         #=> Bag("qux", "bar", "baz", "foo", "foo")

# Difference
say (A - B)         #=> Bag("baz", "foo")
say (B - A)         #=> Bag("qux")

# Symmetric difference
say (A ^ B)         #=> Bag("foo", "qux", "baz")

# Concatenation
say (A + B)         #=> Bag("foo", "foo", "foo", "bar", "bar", "baz", "qux")
```

## Updating the bag

The methods `bag.add_pair(obj, count)` and `bag.update_pair(obj, count)` can be used for efficiently updating a bag in-place.

```ruby
var A = Bag('foo', 'foo', 'bar')

# Add 'bar' with count=2
A.add_pair('baz', 2)

say A   #=> Bag("baz", "baz", "bar", "foo", "foo")

# Update the count of 'foo'
A.update_pair('foo', 1)

say A   #=> Bag("baz", "baz", "bar", "foo")
```

Furthermore, the method `bag.delete(obj)` can be used for removing one occurrence of object `obj` from the bag, while the `.delete_all(obj)` can be used for removing all the occurrences of `obj` from the bag.
