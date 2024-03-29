[1]: https://rosettacode.org/wiki/Negative_base_numbers

# [Negative base numbers][1]

```ruby
func EncodeNegBase(Num n, Num b { .~~ (-36 .. -2) }) {
    var out = []
    var r = 0
    while (n) {
        (n, r) = divmod(n, b)
        if (r < 0) {
            n += 1
            r -= b
        }
        out << r.base(-b)
    }
    return (out.join.flip || "0")
}
 
func DecodeNegBase(Str s, Num b { .~~ (-36 .. -2) }) {
    var total = 0
    for i,c in (s.flip.chars.kv) {
        total += (Num(c, -b) * b**i)
    }
    return total
}
 
say (" 10 in base  -2: ", EncodeNegBase(10, -2))
say ("146 in base  -3: ", EncodeNegBase(146, -3))
say (" 15 in base -10: ", EncodeNegBase(15, -10))
 
say '-'*25
 
say ("11110 from base  -2: ", DecodeNegBase("11110", -2))
say ("21102 from base  -3: ", DecodeNegBase("21102", -3))
say ("  195 from base -10: ", DecodeNegBase("195",  -10))
 
say '-'*25
 
# Extra
say ("25334424 in base -31: ", EncodeNegBase(25334424, -31))
say ("sidef  from base -31: ", DecodeNegBase("sidef", -31))
```

#### Output:
```
 10 in base  -2: 11110
146 in base  -3: 21102
 15 in base -10: 195
-------------------------
11110 from base  -2: 10
21102 from base  -3: 146
  195 from base -10: 15
-------------------------
25334424 in base -31: sidef
sidef  from base -31: 25334424
```
