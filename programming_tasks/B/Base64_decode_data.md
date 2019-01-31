[1]: https://rosettacode.org/wiki/Base64_decode_data

# [Base64 decode data][1]

```ruby
var data = <<'EOT'
VG8gZXJyIGlzIGh1bWFuLCBidXQgdG8gcmVhbGx5IGZvdWwgdGhpbmdzIHVwIHlvdSBuZWVkIGEgY2
9tcHV0ZXIuCiAgICAtLSBQYXVsIFIuIEVocmxpY2g=
EOT
 
say data.decode_base64
```

#### Output:
```
To err is human, but to really foul things up you need a computer.
    -- Paul R. Ehrlich
```