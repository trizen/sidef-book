[1]: https://rosettacode.org/wiki/Variable-length_quantity

# [Variable-length quantity][1]

```ruby
func vlq_encode(num) {
    var t = (0x7F & num)
    var str = t.chr
    while (num >>= 7) {
       t = (0x7F & num)
       str += chr(0x80 | t)
    }
    str.reverse
}
 
func vlq_decode(str) {
    var num = ''
    str.each_byte { |b|
        num += ('%07b' % (b & 0x7F))
    }
    Num(num, 2)
}
 
var tests = [0,   0xa,   123,   254,   255,   256,
             257, 65534, 65535, 65536, 65537, 0x1fffff,
             0x200000]
 
tests.each { |t|
    var vlq = vlq_encode(t)
    printf("%8s %12s %8s\n", t,
        vlq.bytes.join(':', { "%02X" % _ }), vlq_decode(vlq))
}
```

#### Output:
```
       0           00        0
      10           0A       10
     123           7B      123
     254        81:7E      254
     255        81:7F      255
     256        82:00      256
     257        82:01      257
   65534     83:FF:7E    65534
   65535     83:FF:7F    65535
   65536     84:80:00    65536
   65537     84:80:01    65537
 2097151     FF:FF:7F  2097151
 2097152  81:80:80:00  2097152
```