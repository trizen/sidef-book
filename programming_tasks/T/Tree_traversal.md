[1]: http://rosettacode.org/wiki/Tree_traversal

# [Tree traversal][1]

```ruby
func preorder(t) {
    t ? [t[0], __FUNC__(t[1])..., __FUNC__(t[2])...] : []
}
 
func inorder(t) {
    t ? [__FUNC__(t[1])..., t[0], __FUNC__(t[2])...] : []
}
 
func postorder(t) {
    t ? [__FUNC__(t[1])..., __FUNC__(t[2])..., t[0]] : []
}
 
func depth(t) {
    var a = [t]
    var ret = []
    while (a.len > 0) {
        var v = (a.shift \\ next)
        ret « v[0]
        a += [v[1,2]]
    }
    return ret
}
 
var x = [1,[2,[4,[7]],[5]],[3,[6,[8],[9]]]]
say "pre:   #{preorder(x)}"
say "in:    #{inorder(x)}"
say "post:  #{postorder(x)}"
say "depth: #{depth(x)}"
```

#### Output:
```
pre:   1 2 4 7 5 3 6 8 9
in:    7 4 2 5 1 8 6 9 3
post:  7 4 5 2 8 9 6 3 1
depth: 1 2 3 4 5 6 7 8 9
```
