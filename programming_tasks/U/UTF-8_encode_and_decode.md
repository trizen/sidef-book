[1]: http://rosettacode.org/wiki/UTF-8_encode_and_decode

# [UTF-8 encode and decode][1]

```ruby
func utf8_encoder(Number code) {
    code.chr.encode('UTF-8').bytes.map{.chr}
}
 
func utf8_decoder(Array bytes) {
    bytes.map{.ord}.decode('UTF-8')
}
 
for n in ([0x0041, 0x00F6, 0x0416, 0x20AC, 0x1D11E]) {
    var encoded = utf8_encoder(n)
    var decoded = utf8_decoder(encoded)
    assert_eq(n, decoded.ord)
    say "#{decoded} -> #{encoded}"
}
```

#### Output:
```
A -> ["A"]
ö -> ["\xC3", "\xB6"]
Ж -> ["\xD0", "\x96"]
€ -> ["\xE2", "\x82", "\xAC"]
𝄞 -> ["\xF0", "\x9D", "\x84", "\x9E"]
```