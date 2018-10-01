# Hash

An Hash is a dynamic collection of key-value pairs. The keys must be of type String, while the values can have any type.

```ruby
Hash(
    a => 1,
    b => 2,
    c => 3,
)
```

## Working with hashes:

Elements of an hash can be accessed with the special syntax `hash{key}` where `key` is a String-convertable object.

```ruby
var hash = Hash(name => 'Sidef')

# Print the value of a key
say hash{"name"}      #=> "Sidef"

# Set a key into the hash
hash{"age"} = 6

# Print the hash
say hash
```

## Existent key

A key can be checked if it exists in a hash using the syntax: `hash.exists(key)`.

## Deleting a key

A key can be deleted from a hash using the syntax: `hash.delete(key)`.
