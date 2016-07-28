[1]: http://rosettacode.org/wiki/Longest_common_prefix

# [Longest common prefix][1]

```ruby
# Finds the first point where the tree bifurcates
func find_common_prefix(hash, acc) {
    if (hash.len == 1) {
        var pair = hash.to_a[0]
        return __FUNC__(pair.value, acc+pair.key)
    }
    return acc
}

# Creates a tree like: {a => {b => {c => {}}}}
func lcp(*strings) {
    var hash = Hash()

    for str in (strings.sort_by{.len}) {
        var ref = hash
        str.is_empty && return ''
        for char in str {
            if (ref.contains(char)) {
                ref = ref{char}
                ref.len == 0 && break
            }
            else {
                ref = (ref{char} = Hash())
            }
        }
    }

    return find_common_prefix(hash, '')
}
```


Demonstration:

```ruby
var data = [
  ["interspecies","interstellar","interstate"],
  ["throne","throne"],
  ["throne","dungeon"],
  ["throne","","throne"],
  ["cheese"],
  [""],
  [],
  ["prefix","suffix"],
  ["foo","foobar"]
]

for set in data {
    say "lcp(#{set.dump.substr(1,-1)}) = #{lcp(set...).dump}"
}
```

#### Output:
```
lcp("interspecies", "interstellar", "interstate") = "inters"
lcp("throne", "throne") = "throne"
lcp("throne", "dungeon") = ""
lcp("throne", "", "throne") = ""
lcp("cheese") = "cheese"
lcp("") = ""
lcp() = ""
lcp("prefix", "suffix") = ""
lcp("foo", "foobar") = "foo"
```
