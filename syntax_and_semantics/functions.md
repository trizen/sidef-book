# Functions

Like mathematical functions, Sidef's functions can be recursive, take arguments and return values.

```ruby
func hello (name) {
   say "Hello, #{name}!"
}

hello("Sidef")
```

The special `__FUNC__` keyword refers to the current function:

```ruby
func factorial (n) {
   if (n > 1) {
       return (n * __FUNC__(n - 1))
   }
   return 1
}

say factorial(5)     # prints: 120
```

## Closures

In Sidef, all functions are first-class objects which can be passed around like any other object. Additionally, all functions (including methods) are lexical closures.

```ruby
func curry(f, *args1) {
    func (*args2) {
        f(args1..., args2...)
    }
}

func add(a, b) {
    a + b
}

var adder = curry(add, 1)
say adder(3)                #=> 4
```

## Caching functions

By specifying the `cached` trait in a function (or method) declaration, Sidef will automatically cache it for you.

```ruby
func fib(n) is cached {
    return n if (n <= 1)
    fib(n-1) + fib(n-2)
}
say fib(100)              #=> 354224848179261915075
```

## Optional arguments

The parameters of a function can also be declared with a default value, which provides support for optional arguments.

```ruby
func hello (name="Sidef") {
    say "Hello, #{name}!"
}

hello()           # prints: "Hello, Sidef!"
hello("World")    # prints: "Hello, World!"
```

The default value of a parameter is evaluated only when an argument is not provided for that particular parameter, and it can be any arbitrary expression:

```ruby
func foo (a = 1.25.sqrt, b = 1/2) {
     a + b
}

say foo()           # prints the result of: sqrt(1.25) + 1/2
say foo(21, 21)     # prints: 42
```

## Named parameters

This is a very nice feature borrowed from Perl 6 which allows a function to be called with named parameters, giving us the flexibility to put the arguments in no specific order:

```ruby
func divide(a, b) {
   a / b
}

say divide(b: 5, a: 35)  # prints: 7
```

## Variadic functions

A slurpy variable in the form of `*name` can be used as a function parameter to collect the remaining arguments inside an array:

```ruby
func f(*args) {
   say args       #=> [1, 2, 3]
}

f(1, 2, 3)
```

Alternatively, by using a named variable in the form of `:name`, the arguments are collected inside an hash:

```ruby
func f(:pairs) {
   say pairs      #=> Hash(a=>1, b=>2)
}

f(a => 1, b => 2)
```

## Typed parameters

A function can be declared with typed parameters, which are checked at run-time.

```ruby
func concat(String a, String b) {
    a + b
}
```

Now, the function can only be called with strings as arguments:

```ruby
say concat("o", "k")  # ok
say concat(1, 2)      # runtime error
```

The typed parameters require a specific type of object, but they do not default to anything when no value is provided. This means that all typed-parameters are mandatory, unless a default value is provided:

```ruby
func concat(String a="foo", String b="bar") {
   a + b
}

say concat()          # prints: "foobar"
say concat("mini")    # prints: "minibar"
say concat(1, 2)      # this is still a run-time error
```
