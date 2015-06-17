[1]: http://rosettacode.org/wiki/Doubly-linked_list/Element_definition

# [Doubly-linked list/Element definition][1]

```ruby
var node = :(
     data => 'say what',
     next => foo_node,
     prev => bar_node,
);
 
node[:next] = quux_node;  # mutable
```