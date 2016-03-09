[1]: http://rosettacode.org/wiki/RSA_code

# [RSA code][1]

```ruby
const n = 9516311845790656153499716760847001433441357
const e = 65537
const d = 5617843187844953170308463622230283376298685
 
module Message {
    var alphabet = [('A' .. 'Z')..., ' ']
    var rad = alphabet.len
    var code = Hash(^rad -> map {|i| (alphabet[i], i) }...)
    func encode(String t) {
        [code{t.reverse.chars...}] ~Z* t.len.range.map { |i| rad**i } -> sum(0)
    }
    func decode(Number n) {
        ''.join(alphabet[
            gather {
                loop {
                    var (d, m) = n.divmod(rad)
                    take(m)
                    break if (n < rad)
                    n = d
                }
            }...]
        ).reverse
    }
}
 
var secret_message = "ROSETTA CODE"
say "Secret message is #{secret_message}"
 
var numeric_message = Message::encode(secret_message)
say "Secret message in integer form is #{numeric_message}"
 
var numeric_cipher = expmod(numeric_message, e, n)
say "After exponentiation with public exponent we get: #{numeric_cipher}"
 
var text_cipher = Message::decode(numeric_cipher)
say "This turns into the string #{text_cipher}"
 
var numeric_cipher2 = Message::encode(text_cipher)
say "If we re-encode it in integer form we get #{numeric_cipher2}"
 
var numeric_message2 = expmod(numeric_cipher2, d, n)
say "After exponentiation with SECRET exponent we get: #{numeric_message2}"
 
var secret_message2 = Message::decode(numeric_message2)
say "This turns into the string #{secret_message2}"
```

#### Output:
```
Secret message is ROSETTA CODE
Secret message in integer form is 97525102075211938
After exponentiation with public exponent we get: 8326171774113983822045243488956318758396426
This turns into the string ZULYDCEZOWTFXFRRNLIMGNUPHVCJSX
If we re-encode it in integer form we get 8326171774113983822045243488956318758396426
After exponentiation with SECRET exponent we get: 97525102075211938
This turns into the string ROSETTA CODE
```