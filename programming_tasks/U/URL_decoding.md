[1]: https://rosettacode.org/wiki/URL_decoding

# [URL decoding][1]

```ruby
func urldecode(str) {
    str.gsub!('+', ' ')
    str.gsub!(/\%([A-Fa-f0-9]{2})/, {|a| 'C'.pack(a.hex) })
    return str
}
 
say urldecode('http%3A%2F%2Ffoo+bar%2F')   #=> "http://foo bar/"
```
