[1]: http://rosettacode.org/wiki/Fibonacci_sequence

# [Fibonacci sequence][1]

```ruby
func fib_iter(n) {
    var fib = [1, 1];
    (n - fib.len).times {
        fib = [fib[-1], fib[-2] + fib[-1]]
    };
    fib[-1];
}
```
```ruby
func fib_rec(n) {
    n < 2 ? n : (__FUNC__(n-1) + __FUNC__(n-2));
}
```
```ruby
func fib_mem (n) is cached {
    n < 2 ? n : (__FUNC__(n-1) + __FUNC__(n-2));
}
```
```ruby
func fib_closed(n) {
    define S = (1.25.sqrt + 0.5);
    define T = (-S + 1);
    (S**n - T**n) / (-T + S) -> roundf(0);
}
```