[1]: https://rosettacode.org/wiki/Substring/Top_and_tail

# [Substring/Top and tail][1]

Strip any characters:

```ruby
say "knight".substr(1)        # strip first character
say "socks".substr(0, -1)     # strip last character
say "brooms".substr(1, -1)    # strip both first and last characters
say "与今令".substr(1, -1)     # => 今
```

#### Output:
```
night
sock
room
今
```


Strip graphemes:

```ruby
var gstr = "J\x{332}o\x{332}s\x{332}e\x{301}\x{332}"
say gstr-/^\X/                     # strip first grapheme
say gstr-/\X\z/                    # strip last grapheme
say gstr.sub(/^\X/).sub(/\X\z/)    # strip both first and last graphemes
```

#### Output:
```
o̲s̲é̲
J̲o̲s̲
o̲s̲
```
