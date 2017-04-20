[1]: http://rosettacode.org/wiki/Caesar_cipher

# [Caesar cipher][1]

```ruby
func caesar(msg, key, decode=false) {
    decode && (key = (26 - key))
    msg.gsub(/([A-Z])/i, {|c| ((c.uc.ord - 65 + key) % 26) + 65 -> chr})
}
 
var msg = 'THE FIVE BOXING WIZARDS JUMP QUICKLY'
 
var enc = caesar(msg, 10)
var dec = caesar(enc, 10, true)
 
say "msg: #{msg}"
say "enc: #{enc}"
say "dec: #{dec}"
```

#### Output:
```
msg: THE FIVE BOXING WIZARDS JUMP QUICKLY
enc: DRO PSFO LYHSXQ GSJKBNC TEWZ AESMUVI
dec: THE FIVE BOXING WIZARDS JUMP QUICKLY
```
