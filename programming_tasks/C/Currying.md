[1]: http://rosettacode.org/wiki/Currying

# [Currying][1]

This can be done by using lazy methods:

```ruby
var adder = 1.method(:add)
say adder(3)                 #=> 4
```


Or by using a generic curry function:

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
say adder(3)                 #=>4
```
