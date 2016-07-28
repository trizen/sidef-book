[1]: http://rosettacode.org/wiki/Multisplit

# [Multisplit][1]

```ruby
func multisplit(sep, str, keep_sep=false) {
    sep = sep.map{.escape}.join('|');
    var re = Regex(keep_sep ? "(#{sep})" : sep);
    str.split(re, -1);
}
 
[false, true].each { |bool|
    say multisplit(%w(== != =), 'a!===b=!=c', keep_sep: bool);
}
```

#### Output:
```
["a", "", "b", "", "c"]
["a", "!=", "", "==", "b", "=", "", "!=", "c"]
```
