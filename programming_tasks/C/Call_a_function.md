[1]: http://rosettacode.org/wiki/Call_a_function

# [Call a function][1]

All functions in Sidef are first-class closures

```ruby
foo()                        # without arguments
foo(1, 2)                    # with two arguments
foo(args...)                 # with a variable number of arguments
foo(name: 'Bar', age: 42)    # with named arguments
 
var f = foo                  # store the function foo in variable 'f'
var result = f()             # obtain the return value of a function
 
var arr = [1,2,3]
foo(arr)                     # the arguments are passed by object-reference
```


Partial application is possible by using a curry function:

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
say adder(3)                  #=>4
```
