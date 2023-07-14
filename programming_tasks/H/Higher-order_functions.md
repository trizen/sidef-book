[1]: https://rosettacode.org/wiki/Higher-order_functions

# [Higher-order functions][1]

```ruby
func first(f) {
  return f()
}
 
func second {
  return "second"
}
 
say first(second)               # => "second"
say first(func { "third" })     # => "third"
```
