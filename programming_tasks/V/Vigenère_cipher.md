[1]: https://rosettacode.org/wiki/Vigenère_cipher

# [Vigenère cipher][1]

```ruby
func s2v(s) { s.uc.scan(/[A-Z]/).map{.ord} »-» 65 }
func v2s(v) { v »%» 26 »+» 65 -> map{.chr}.join   }
 
func blacken (red, key) { v2s(s2v(red) »+« s2v(key)) }
func redden  (blk, key) { v2s(s2v(blk) »-« s2v(key)) }
 
var red = "Beware the Jabberwock, my son! The jaws that bite, the claws that catch!"
var key = "Vigenere Cipher!!!"
 
say red
say (var black = blacken(red, key))
say redden(black, key)
```

#### Output:
```
Beware the Jabberwock, my son! The jaws that bite, the claws that catch!
WMCEEIKLGRPIFVMEUGXQPWQVIOIAVEYXUEKFKBTALVXTGAFXYEVKPAGY
BEWARETHEJABBERWOCKMYSONTHEJAWSTHATBITETHECLAWSTHATCATCH
```
