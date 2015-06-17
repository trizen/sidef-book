[1]: http://rosettacode.org/wiki/Longest_common_prefix

# [Longest common prefix][1]

```ruby
# Finds the first point where the tree bifurcates
func find_common_prefix(hash, acc) {
    if ((var keys = hash.keys).len == 1) {
        return __FUNC__(hash[keys[0]], acc+keys[0]);
    };
    return acc;
}
 
# Creates a tree like: {a => {b => {c => {}}}}
func lcp(*strings) {
    var hash = Hash.new;
 
    strings.sort {|a,b| a.len <=> b.len}.each { |str|
        var ref = hash;
        str == '' && return '';
        str.each { |char|
            if (ref.has_key(char)) {
                ref = ref[char];
                ref.keys.len == 0 && break;
            } else {
                ref = (ref[char] = Hash.new);
            }
        };
    };
 
    return find_common_prefix(hash, '');
};
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
];
 
data.each { |set|
    say "lcp(#{set.dump.substr(1,-1)}) = #{lcp(set...).dump}";
};
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