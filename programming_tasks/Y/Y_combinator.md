[1]: https://rosettacode.org/wiki/Y_combinator

# [Y combinator][1]

```ruby
var y = ->(f) {->(g) {g(g)}(->(g) { f(->(*args) {g(g)(args...)})})}
 
var fac = ->(f) { ->(n) { n < 2 ? 1 : (n * f(n-1)) } }
say 10.of { |i| y(fac)(i) }
 
var fib = ->(f) { ->(n) { n < 2 ? n : (f(n-2) + f(n-1)) } }
say 10.of { |i| y(fib)(i) }
```

#### Output:
```
[1, 1, 2, 6, 24, 120, 720, 5040, 40320, 362880]
[0, 1, 1, 2, 3, 5, 8, 13, 21, 34]
```
