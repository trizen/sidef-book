[1]: https://rosettacode.org/wiki/Singly-linked_list/Traversal

# [Singly-linked list/Traversal][1]

```ruby
var list = 'a':'b':'c':nil
#var list = ['a', ['b', ['c']]]
#var list = Pair('a', Pair('b', Pair('c', nil)))
 
for (var l = list; l != nil; l = l[1]) {
    say l[0]
}
```

#### Output:
```
a
b
c
```
