# Functional pattern matching

The functional pattern matching it's an extension of the multiple dispatch feature, and allows us to call a certain function or method using values or expressions as patterns, instead of types.

Example:

```ruby
func foo((1)) { say "one" }
func foo((2)) { say "two" }
func foo (n)  { say n }

foo(1)      # calls the first function
foo(2)      # calls the second function
foo(3)      # calls the third function
```

Taking advantage of this feature, we can write the Fibonacci function in the following way:

```ruby
func fib((0)) { 0 }
func fib((1)) { 1 }
func fib (n)  { fib(n-1) + fib(n-2) }

say fib(12)    # prints: 144
```

In addition, instead of an expression, we can specify a block of code, which will get called with the value of the argument for checking:

```ruby
func fib({.is_neg})  { NaN }
func fib({.is_zero}) { 0 }
func fib({.is_one})  { 1 }
func fib(n)          { fib(n-1) + fib(n-2) }

say fib(12)    # prints: 144
```

To keep the value of the argument, we can specify a name for the parameter in front of the block used for pattern matching:

```ruby
func fib(n { _ <= 1 }) { n }
func fib(n)            { fib(n-1) + fib(n-2) }

say fib(12)    # prints: 144
```

Pattern matching is available for methods as well:

```ruby
class Ackermann {
    method A({ .is_zero }, n) {
        n + 1
    }

    method A(m, (0)) {
        self.A(m-1, 1)
    }

    method A(m, n) {
        self.A(m-1, self.A(m, n-1))
    }
}

var obj = Ackermann()
say obj.A(3, 2)             # prints: 29
```
