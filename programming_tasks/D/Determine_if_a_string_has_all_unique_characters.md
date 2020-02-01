[1]: https://rosettacode.org/wiki/Determine_if_a_string_has_all_unique_characters

# [Determine if a string has all unique characters][1]

```ruby
func index_duplicates(str) {
    gather {
        for k,v in (str.chars.kv) {
            var i = str.index(v, k+1)
            take([k, i]) if (i != -1)
        }
    }
}
 
var strings = [
    "", ".", "abcABC", "XYZ ZYX",
    "1234567890ABCDEFGHIJKLMN0PQRSTUVWXYZ",
    "01234567890ABCDEFGHIJKLMN0PQRSTUVWXYZ0X",
    "hétérogénéité", "🎆🎃🎇🎈", "😍😀🙌💃😍🙌",
    "🐠🐟🐡🦈🐬🐳🐋🐡"
]
 
strings.each {|str|
    print "\n'#{str}' (size: #{str.len}) "
    var dups = index_duplicates(str)
    say "has duplicated characters:" if dups
    for i,j in (dups) {
        say "#{str[i]} (#{'%#x' % str[i].ord}) in positions: #{i}, #{j}"
    }
    say "has no duplicates." if !dups
}
```

#### Output:
```
'' (size: 0) has no duplicates.

'.' (size: 1) has no duplicates.

'abcABC' (size: 6) has no duplicates.

'XYZ ZYX' (size: 7) has duplicated characters:
X (0x58) in positions: 0, 6
Y (0x59) in positions: 1, 5
Z (0x5a) in positions: 2, 4

'1234567890ABCDEFGHIJKLMN0PQRSTUVWXYZ' (size: 36) has duplicated characters:
0 (0x30) in positions: 9, 24

'01234567890ABCDEFGHIJKLMN0PQRSTUVWXYZ0X' (size: 39) has duplicated characters:
0 (0x30) in positions: 0, 10
0 (0x30) in positions: 10, 25
0 (0x30) in positions: 25, 37
X (0x58) in positions: 34, 38

'hétérogénéité' (size: 13) has duplicated characters:
é (0xe9) in positions: 1, 3
t (0x74) in positions: 2, 11
é (0xe9) in positions: 3, 7
é (0xe9) in positions: 7, 9
é (0xe9) in positions: 9, 12

'🎆🎃🎇🎈' (size: 4) has no duplicates.

'😍😀🙌💃😍🙌' (size: 6) has duplicated characters:
😍 (0x1f60d) in positions: 0, 4
🙌 (0x1f64c) in positions: 2, 5

'🐠🐟🐡🦈🐬🐳🐋🐡' (size: 8) has duplicated characters:
🐡 (0x1f421) in positions: 2, 7
```
