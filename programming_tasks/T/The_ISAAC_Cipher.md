[1]: http://rosettacode.org/wiki/The_ISAAC_Cipher

# [The ISAAC Cipher][1]

```ruby
require 'Math::Random::ISAAC';
 
func xor_isaac(key, msg) {
  var rng = %s'Math::Random::ISAAC'.new(unpack('C*', key));
 
  msg.chars»ord»()
    »^« 256.of{ rng.irand % 95 + 32 }.last(msg.len).reverse
    «%« '%02X' -> join;
}
 
var msg = 'a Top Secret secret';
var key = 'this is my secret key';
 
var enc = xor_isaac(key, msg);
var dec = xor_isaac(key, pack('H*', enc));
 
say "Message: #{msg}";
say "Key    : #{key}";
say "XOR    : #{enc}";
say "XOR dcr: #{pack('H*', dec)}";
```

#### Output:
```
Message: a Top Secret secret
Key    : this is my secret key
XOR    : 1C0636190B1260233B35125F1E1D0E2F4C5422
XOR dcr: a Top Secret secret
```