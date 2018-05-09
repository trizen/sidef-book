[1]: https://rosettacode.org/wiki/Substitution_Cipher

# [Substitution Cipher][1]

```ruby
module SubstitutionCipher {
 
    const key = %c"]kYV}(!7P$n5_0i R:?jOWtF/=-pe'AD&@r6%ZXs\"v*N[#wSl9zq2^+g;LoB`aGh{3.HIu4fbK)mU8|dMET><,Qc\\C1yxJ"
 
    func encode(String s) {
        var r = ""
        s.each {|c|
            r += key[c.ord - 32]
        }
        return r
    }
 
    func decode(String s) {
        var r = ""
        s.each {|c|
            r += (key.first_index { _ == c } + 32 -> chr)
        }
        return r
    }
}
 
 
with ("The quick brown fox jumps over the lazy dog, who barks VERY loudly!") { |s|
    var enc = SubstitutionCipher::encode(s)
    var dec = SubstitutionCipher::decode(enc)
    say("Original: ", s, "\n -> Encoded: ", enc, "\n -> Decoded: ", dec)
}
```

#### Output:
```
Original: The quick brown fox jumps over the lazy dog, who barks VERY loudly!
 -> Encoded: 2bu]E,KHm].Tdc|]4d\]),8M>]dQuT]<bu]U31C]Idf_]cbd].3Tm>]+ZzL]Ud,IUCk
 -> Decoded: The quick brown fox jumps over the lazy dog, who barks VERY loudly!
```