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

More efficient implementation, running in **O(n*log(n))** time, using **O(n)** space:

```ruby
define LOOKAHEAD_LEN = 128

func bwt_sort (String s) {    # O(n * LOOKAHEAD_LEN) space (fast)

    ^s.len -> map {|i|
        var t = s.slice(i, LOOKAHEAD_LEN)

        if (t.len < LOOKAHEAD_LEN) {
            t += s.slice(0, min(i, LOOKAHEAD_LEN - t.len))
        }

        [t, i]
    }.sort {|a,b|
        (a[0] <=> b[0]) || (s.rotate(a[1]) <=> s.rotate(b[1]))
    }.map { .[1] }
}

func bwt_encode(String s) {

    var bwt    = bwt_sort(s)
    var ret    = bwt.map {|i| s.slice(i-1, 1) }.join
    var prefix = s.slice(0, LOOKAHEAD_LEN)
    var len    = prefix.len

    var idx = 0;
    for i in (bwt) {

        var lookahead = s.slice(i, len)

        if (lookahead.len < len) {
            lookahead += s.slice(0, len - lookahead.len)
        }

        if (lookahead == prefix) {
            var row = s.rotate(i)
            if (row == s) {
                break
            }
        }
        ++idx
    }

    return (ret, idx)
}

func bwt_decode(String bwt, Number idx) {    # fast inversion

    var tail = bwt.chars
    var head = tail.sort

    var indices = Hash()
    tail.each_kv {|i,v|
        indices{v} := [] << i
    }

    var table = []
    head.each_kv {|i,v|
        table[i] = indices{v}.shift
    }

    var dec = ''
    var i = idx

    head.len.times {
        dec += head[i]
        i = table[i]
    }

    return dec
}

var tests = [
    "banana", "appellee", "dogwood", "TOBEORNOTTOBEORTOBEORNOT"
    "SIX.MIXED.PIXIES.SIFT.SIXTY.PIXIE.DUST.BOXES",
]

tests.each { |str|
    var (enc, idx) = bwt_encode(str)
    var dec = bwt_decode(enc, idx)
    say "BWT(#{dec.dump}) = (#{enc.dump}, #{idx})"
    assert_eq(str, dec)
}
```

