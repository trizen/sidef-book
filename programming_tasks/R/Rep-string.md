[1]: http://rosettacode.org/wiki/Rep-string

# [Rep-string][1]

```ruby
var arr = <1001110011 1110111011
           0010010010 1010101010
           1111111111 0100101101
           0100100  101  11 00 1>
 
for n (arr) {
    if (var m = /^(.+)\1+(.*$)(?(?{ substr($1, 0, length $2) eq $2 })|(?!))/.match(n)) {
       var i = m[0].len
       say (n.substr(0, i),
            n.substr(i, i).tr('01', '𝟘𝟙'),
            n.substr(i*2))
    } else {
        say "#{n} (no repeat)"
    }
}
```

#### Output:
```
10011𝟙𝟘𝟘𝟙𝟙
1110𝟙𝟙𝟙𝟘11
001𝟘𝟘𝟙0010
1010𝟙𝟘𝟙𝟘10
11111𝟙𝟙𝟙𝟙𝟙
0100101101 (no repeat)
010𝟘𝟙𝟘0
101 (no repeat)
1𝟙
0𝟘
1 (no repeat)
```
