[1]: https://rosettacode.org/wiki/Determine_if_a_string_has_all_the_same_characters

# [Determine if a string has all the same characters][1]

```ruby
func analyze_string(str) {
    var chars = str.chars
    chars.range.to_a.each_cons(2, {|a,b|
        chars[a] == chars[b] || return b
    })
    return str.len
}
 
var strings = ["", "   ", "2", "333", ".55", "tttTTT", "4444   444k", "pépé", "🐶🐶🐺🐶", "🎄🎄🎄🎄"]
 
strings.each {|str|
    print "'#{str}' (size #{str.len}): "
    var idx = analyze_string(str)
 
    if (idx == str.len) {
        say "all the same."
    }
    else {
        say "first different char '#{str[idx]}' (#{'%#x' % str[idx].ord}) at position #{idx}."
    }
}
```

#### Output:
```
'' (size 0): all the same.
'   ' (size 3): all the same.
'2' (size 1): all the same.
'333' (size 3): all the same.
'.55' (size 3): first different char '5' (0x35) at position 1.
'tttTTT' (size 6): first different char 'T' (0x54) at position 3.
'4444   444k' (size 11): first different char ' ' (0x20) at position 4.
'pépé' (size 4): first different char 'é' (0xe9) at position 1.
'🐶🐶🐺🐶' (size 4): first different char '🐺' (0x1f43a) at position 2.
'🎄🎄🎄🎄' (size 4): all the same.
```
