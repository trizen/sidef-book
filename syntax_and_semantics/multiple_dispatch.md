# Multiple dispatch

Multiple dispatch allows us to declare multiple variants of the same function or method, each working only with a certain type of arguments.

For example, if we declare to functions with the same name, but with different types of parameters, Sidef will decide automatically which function to call:

```ruby
func foo(Number a) {
    say a
}

func foo(String a) {
    say a
}

foo(1234)       # calls the first function
foo("bar")      # calls the second function
```

The functions are checked in the order in which they are declared:

```ruby
func foo(Array a) { ... }       # works with an array
func foo(Hash h)  { ... }       # works with an hash
func foo(any)     { ... }       # works with anything else
```

This is true for methods as well:


```ruby
class Example {
    method foo(Number n, String s) {
        say "first"
    }

    method foo(Array a) {
        say "second"
    }
}

var obj = Example()
obj.foo(1234, "foo")    # calls the first method
obj.foo([1,2,3])        # calls the second method
```
