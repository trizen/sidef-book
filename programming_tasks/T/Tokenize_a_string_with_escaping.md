[1]: http://rosettacode.org/wiki/Tokenize_a_string_with_escaping

# [Tokenize a string with escaping][1]

```ruby
func tokenize(string, sep, esc) {
    var fields = string.split(
        Regex(esc.escape + '.(*SKIP)(*FAIL)|' + sep.escape, 's'), -1
    )
    fields.map{.gsub(Regex(esc + '(.)'), {|s1| s1 }) }
}
 
tokenize("one^|uno||three^^^^|four^^^|^cuatro|", '|', '^').each { |str|
    say str.dump
}
```

#### Output:
```
"one^|uno"
""
"three^^^^"
"four^^^|^cuatro"
""
```