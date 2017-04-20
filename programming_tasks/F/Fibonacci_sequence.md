[1]: http://rosettacode.org/wiki/Fibonacci_sequence

# [Fibonacci sequence][1]

Iterative:

```ruby
func fib_iter(n) {
    var (a, b) = (0, 1)
    { (a, b) = (b, a+b) } * n
    return a
}
```

Recursive:

```ruby
func fib_rec(n) {
    n < 2 ? n : (__FUNC__(n-1) + __FUNC__(n-2))
}
```

Recursive with memoization:
```ruby
func fib_mem (n) is cached {
    n < 2 ? n : (__FUNC__(n-1) + __FUNC__(n-2))
}
```

Closed-form:
```ruby
func fib_closed(n) {
    define S = (1.25.sqrt + 0.5)
    define T = (-S + 1)
    (S**n - T**n) / (-T + S) -> round
}
```

Built-in:
```ruby
say fib(12)        #=> 144
```
