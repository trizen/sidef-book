[1]: https://rosettacode.org/wiki/Visualize_a_tree

# [Visualize a tree][1]

```ruby
func visualize_tree(tree, label, children,
                    indent = '',
                    mids = ['├─', '│ '],
                    ends = ['└─', '  '],
) {
    func visit(node, pre) {
        gather {
            take(pre[0] + label(node))
            var chldn = children(node)
            var end = chldn.end
            chldn.each_kv { |i, child|
                if (i == end) { take(visit(child, [pre[1]] ~X+ ends)) }
                else          { take(visit(child, [pre[1]] ~X+ mids)) }
            }
        }
    }
    visit(tree, [indent] * 2)
}
 
var tree = 'root':['a':['a1':['a11':[]]],'b':['b1':['b11':[]],'b2':[],'b3':[]]]
say visualize_tree(tree, { .first }, { .second }).flatten.join("\n")
```

#### Output:
```
root
├─a
│ └─a1
│   └─a11
└─b
  ├─b1
  │ └─b11
  ├─b2
  └─b3
```