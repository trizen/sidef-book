[1]: http://rosettacode.org/wiki/Associative_array/Iteration

# [Associative array/Iteration][1]

```ruby
var hash = Hash.new(
    key1 => 'value1',
    key2 => 'value2',
)
 
# Iterate over key-value pairs
hash.each { |key, value|
    say "#{key}: #{value}";
}
 
# Iterate only over keys
hash.keys.each { |key|
    say key;
}
 
# Iterate only over values
hash.values.each { |value|
    say value;
}
```

#### Output:
```
key1: value1
key2: value2
key1
key2
value1
value2
```