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

## Hash of Arrays

The idiom `hash{key} := [] << value` can be used for creating an hash of arrays, as illustrated in the example below:

```ruby
var hash = Hash()

for p in (primes(100)) {
    for d in (divisors(p-1)) {
        if (powmod(2, d, p) == 1) {
            hash{d} := [] << p
        }
    }
}

say hash.grep_v { .len > 1 }
```

which outputs:

```
Hash(
    "10" => [11, 31],
    "11" => [23, 89],
    "18" => [19, 73],
    "22" => [23, 89],
    "36" => [37, 73]
)
```

## Existent key

A key can be checked if it exists in a hash using the syntax: `hash.has(key)`.


## Deleting a key

A key can be deleted from a hash using the syntax: `hash.delete(key)`.
