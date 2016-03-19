[1]: http://rosettacode.org/wiki/Read_a_file_character_by_character/UTF8

# [Read a file character by character/UTF8][1]

```ruby
var file = File('input.txt')        # the input file contains: "aă€⼥"
var fh = file.open_r                # equivalent with: file.open('<:utf8')
fh.each_char { |char|
    printf("got character #{char} [U+%04x]\n", char.ord)
}
```

#### Output:
```
got character a [U+0061]
got character ă [U+0103]
got character € [U+20ac]
got character ⼥ [U+2f25]
```