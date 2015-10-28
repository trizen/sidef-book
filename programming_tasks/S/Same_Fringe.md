[1]: http://rosettacode.org/wiki/Same_Fringe

# [Same Fringe][1]

```ruby
var trees = [
    # 0..2 are same
    [ 'd', [ 'c', [ 'a', 'b', ], ], ],
    [ [ 'd', 'c' ], [ 'a', 'b' ] ],
    [ [ [ 'd', 'c', ], 'a', ], 'b', ],
    # and this one's different!
    [ [ [ [ [ [ 'a' ], 'b' ], 'c', ], 'd', ], 'e', ], 'f' ],
];
 
func get_tree_iterator(*rtrees) {
    var tree;
    func {
        tree = rtrees.pop;
        while (defined(tree) && tree.is_an(Array)) {
            rtrees.append(tree[1]);
            tree = tree[0];
        }
        return tree;
    }
}
 
func cmp_fringe(a, b) {
    var ti1 = get_tree_iterator(a);
    var ti2 = get_tree_iterator(b);
    loop {
        var (L, R) = (ti1(), ti2());
         defined(L) &&  defined(R) && (L == R) && next;
        !defined(L) && !defined(R) && return "Same";
        return "Different";
    }
}
 
range(1, trees.end).each { |tree_idx|
    say ("tree[#{tree_idx-1}] vs tree[#{tree_idx}]: ",
           cmp_fringe(trees[tree_idx-1], trees[tree_idx]));
}
```

#### Output:
```
tree[0] vs tree[1]: Same
tree[1] vs tree[2]: Same
tree[2] vs tree[3]: Different
```