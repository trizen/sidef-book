[1]: http://rosettacode.org/wiki/Suffix_tree

# [Suffix tree][1]

```ruby
func suffix_tree(Str t) {
    suffix_tree(^t.len -> map { t.substr(_) })
}

func suffix_tree(Arr a {.len == 1}) {
    Hash(a[0] => nil)
}

func suffix_tree(Arr a) {
    var h = Hash()
    for k,v in (a.group_by { .char(0) }) {
        var subtree = suffix_tree(v.map { .substr(1) })
        var subkeys = subtree.keys
        if (subkeys.len == 1) {
            var subk = subkeys[0]
            h{k + subk} = subtree{subk}
        }
        else {
            h{k} = subtree
        }
    }
    return h
}

say suffix_tree('banana$')
```

#### Output:
```
Hash(
    "$" => nil,
    "a" => Hash(
        "$" => nil,
        "na" => Hash(
            "$" => nil,
            "na$" => nil
        )
    ),
    "banana$" => nil,
    "na" => Hash(
        "$" => nil,
        "na$" => nil
    )
)
```
