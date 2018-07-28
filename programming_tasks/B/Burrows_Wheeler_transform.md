[1]: https://rosettacode.org/wiki/Burrows–Wheeler_transform

# [Burrows–Wheeler transform][1]

```ruby
class BurrowsWheelerTransform (String L = "\002") {
 
    method encode(String s) {
        assert(!s.contains(L), "String cannot contain `#{L.dump}`")
        s = (L + s)
        s.len.of{|i| s.substr(i) + s.substr(0, i) }.sort.map{.last}.join
    }
 
    method decode(String s) {
        var t = s.len.of("")
        var c = s.chars
        { t = (c »+« t).sort } * s.len
        t.first { .begins_with(L) }.substr(L.len)
    }
}
 
var tests = [
    "banana", "appellee", "dogwood", "TOBEORNOTTOBEORTOBEORNOT"
    "SIX.MIXED.PIXIES.SIFT.SIXTY.PIXIE.DUST.BOXES",
]
 
var bwt = BurrowsWheelerTransform(L: '$')
 
tests.each { |str|
    var enc = bwt.encode(str)
    var dec = bwt.decode(enc)
    say "BWT(#{dec.dump}) = #{enc.dump}"
    assert_eq(str, dec)
}
```

#### Output:
```
BWT("banana") = "annb$aa"
BWT("appellee") = "e$elplepa"
BWT("dogwood") = "do$oodwg"
BWT("TOBEORNOTTOBEORTOBEORNOT") = "TOOOBBBRRTTTEEENNOOOOR$TO"
BWT("SIX.MIXED.PIXIES.SIFT.SIXTY.PIXIE.DUST.BOXES") = "STEXYDST.E.IXXIIXXSSMPPS.B..EE.$.USFXDIIOIIIT"
```