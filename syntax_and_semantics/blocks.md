# Blocks

In Sidef, a block of code is an object which encapsulates zero or more expressions and is delimited by a pair of curly braces (`{}`).

```ruby
var block = {
    say "Hello, World!"
}
```

## Block parameters

For declaring block parameters, Sidef borrows Ruby's way of doing this, by using the `|arg1, arg2, ...|` special syntax:

```ruby
{ |a, b|

   say a            # prints: 1
   say b            # prints: 2

}(1, 2)
```

## Callbacks

Blocks are also used as arguments to many built-in methods as callback blocks:

```ruby
{ print "Sidef! " } * 3        # prints "Sidef! Sidef! Sidef! "
5.times {|x| print x }         # prints "01234"
[1,2,3].sort {|a,b| b <=> a }  # returns a new array: [3,2,1]
```

The `Block` class also implements some useful methods, such as:

```ruby
say {|n| n**2 }.map(1..5)        #=> [1, 4, 9, 16, 25]
say { .is_odd }.grep([1,2,3,4])  #=> [1, 3]
```
