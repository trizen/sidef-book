[1]: https://rosettacode.org/wiki/Substring

# [Substring][1]

```ruby
var str = 'abcdefgh'
var n = 2
var m = 3
say str.substr(n, m)                    #=> cde
say str.substr(n)                       #=> cdefgh
say str.substr(0, -1)                   #=> abcdefg
say str.substr(str.index('d'), m)       #=> def
say str.substr(str.index('de'), m)      #=> def
```
