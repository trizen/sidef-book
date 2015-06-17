[1]: http://rosettacode.org/wiki/Topic_variable

# [Topic variable][1]

The topic variable *_* is defined at compile-time in every block of a program. To call a method on it, you can just use the prefix operator _.method_name_ which is the same as __.method_name_.

```ruby
[9,16,25].map {.sqrt};   # new array: [3, 4, 5]
```