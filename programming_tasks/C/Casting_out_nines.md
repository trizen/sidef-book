[1]: https://rosettacode.org/wiki/Casting_out_nines

# [Casting out nines][1]

```ruby
func cast_out(base = 10, min = 1, max = (base**2 - 1)) {
 
    var b9  = base-1
    var ran = b9.range.grep {|n| n%b9 == (n*n % b9) }
 
    var x = min//b9
    var r = []
 
    loop {
        ran.each {|n|
            var k = (b9*x + n)
            return r if (k > max)
            r << k if (k >= min)
        }
        ++x
    }
 
    return r
}
 
say cast_out().join(' ')
say cast_out(16).join(' ')
say cast_out(17).join(' ')
```

#### Output:
```
1 9 10 18 19 27 28 36 37 45 46 54 55 63 64 72 73 81 82 90 91 99
1 6 10 15 16 21 25 30 31 36 40 45 46 51 55 60 61 66 70 75 76 81 85 90 91 96 100 105 106 111 115 120 121 126 130 135 136 141 145 150 151 156 160 165 166 171 175 180 181 186 190 195 196 201 205 210 211 216 220 225 226 231 235 240 241 246 250 255
1 16 17 32 33 48 49 64 65 80 81 96 97 112 113 128 129 144 145 160 161 176 177 192 193 208 209 224 225 240 241 256 257 272 273 288
```