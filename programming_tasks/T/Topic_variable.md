[1]: http://rosettacode.org/wiki/Topic_variable

# [Topic variable][1]

The underscore (\_) topic variable is defined at compile-time in every block of a program. To call a method on it, we can just use the prefix dot (*.*) operator, followed by a method name, which is equivalent with *\_.method*

```ruby
say [9,16,25].map{ .sqrt }   # prints: [3, 4, 5]
```
