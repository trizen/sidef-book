# for

The `for` construct it's usually used for iteration over collections and for counting.

The following loop counts from 0 to 9:

```ruby
for (var i = 0; i < 10; i++) {
    say i
}
```

Alternatively, using a simpler form of the for-loop:

```ruby
for (0 ..^ 10) { |i|
    say i
}
```

To iterate over an array, Sidef supports yet another form of the `for` loop:

```ruby
for i in [1,2,3,4] {
    say i
}
```

The `for-in` loop is a generalization of the `for` loop, supporting iteration over any object that respond to the `iter` method, which must return a block as the iterator, and the block should return one value at a time when it's called, or `nil` when there are no other values to return, which will break the loop.

Alternatively, the object may also respond to the `to_a` method, which must return an object of type `Array`. Using this knowledge, we can iterate over `Hash` objects because the `Hash` class implements the `to_a` method:

```ruby
for i,k in Hash(a => 1, b => 2) {
    say "<#{i}> <#{k}>"
}
```

The `for-in` loop can also be used in iterating over matrices:

```ruby
for i,j,k in [
    %w(a b c),
    %w(d e f),
] {
    say "<#{i}> <#{j}> <#{k}>"
}
```
