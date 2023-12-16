[1]: https://rosettacode.org/wiki/Decorate-sort-undecorate_idiom

# [Decorate-sort-undecorate idiom][1]

```ruby
var str = "Rosetta Code is a programming chrestomathy site"

# Built-in
say str.split.sort_by{.len}

# Same thing explicitly
say str.split.map {|w| [w, w.len] }.sort{|a,b| a[1] <=> b[1] }.map { _[0] }

# Sort by word length, then lexical:
var str2 = str+" seven extra words added to this demo"
say str2.split.sort_by{|word| [word.len, word] }
```

#### Output:
```
["a", "is", "Code", "site", "Rosetta", "programming", "chrestomathy"]
["a", "is", "Code", "site", "Rosetta", "programming", "chrestomathy"]
["a", "is", "to", "Code", "demo", "site", "this", "added", "extra", "seven", "words", "Rosetta", "programming", "chrestomathy"]
```
