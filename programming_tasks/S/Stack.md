[1]: http://rosettacode.org/wiki/Stack

# [Stack][1]

Using a built-in array:

```ruby
var stack = [];
stack.push(42);         # pushing
say stack.pop;          # popping
say stack.is_empty;     # is_emtpy?
```


Creating a Stack class:

```ruby
class Stack {
    def stack = [];
    method pop        { stack.pop };
    method push(item) { stack.push(item) };
    method empty      { stack.is_empty };
}
 
var stack = Stack();
stack.push(42);
say stack.pop;          # => 42
say stack.empty;        # => true
```