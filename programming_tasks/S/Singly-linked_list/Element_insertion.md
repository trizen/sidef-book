[1]: http://rosettacode.org/wiki/Singly-linked_list/Element_insertion

# [Singly-linked list/Element insertion][1]

```ruby
func insert_after(a,b) {
    b[:next] = a[:next];
    a[:next] = b;
}
 
var B = :(
    data => 3,
    next => nil,    # not a circular list
);
var A = :(
    data => 1,
    next => B,
);
var C = :(
    data => 2,
);
 
insert_after(A, C);
```