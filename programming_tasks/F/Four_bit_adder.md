[1]: http://rosettacode.org/wiki/Four_bit_adder

# [Four bit adder][1]

```ruby
func bxor(a, b) {
  (~a & b) | (a & ~b)
}

func half_adder(a, b) {
  return (bxor(a, b), a & b)
}

func full_adder(a, b, c) {
  var (s1, c1) = half_adder(a, c)
  var (s2, c2) = half_adder(s1, b)
  return (s2, c1 | c2)
}

func four_bit_adder(a, b) {
  var (s0, c0) = full_adder(a[0], b[0], 0)
  var (s1, c1) = full_adder(a[1], b[1], c0)
  var (s2, c2) = full_adder(a[2], b[2], c1)
  var (s3, c3) = full_adder(a[3], b[3], c2)
  return ([s3,s2,s1,s0].join, c3.to_s)
}

say " A    B      A      B   C    S  sum"
for a in ^16 {
  for b in ^16 {
    var(abin, bbin) = [a,b].map{|n| "%04b"%n->chars.flip.map{.to_i} }...
    var(s, c) = four_bit_adder(abin, bbin)
    printf("%2d + %2d = %s + %s = %s %s = %2d\n",
        a, b, abin.join, bbin.join, c, s, "#{c}#{s}".bin)
    }
}
```

#### Output:
```
 A    B      A      B   C    S  sum
 0 +  0 = 0000 + 0000 = 0 0000 =  0
 0 +  1 = 0000 + 0001 = 0 0001 =  1
 0 +  2 = 0000 + 0010 = 0 0010 =  2
 0 +  3 = 0000 + 0011 = 0 0011 =  3
 0 +  4 = 0000 + 0100 = 0 0100 =  4
...
 7 + 13 = 0111 + 1101 = 1 0100 = 20
 7 + 14 = 0111 + 1110 = 1 0101 = 21
 7 + 15 = 0111 + 1111 = 1 0110 = 22
 8 +  0 = 1000 + 0000 = 0 1000 =  8
 8 +  1 = 1000 + 0001 = 0 1001 =  9
 8 +  2 = 1000 + 0010 = 0 1010 = 10
...
15 + 12 = 1111 + 1100 = 1 1011 = 27
15 + 13 = 1111 + 1101 = 1 1100 = 28
15 + 14 = 1111 + 1110 = 1 1101 = 29
15 + 15 = 1111 + 1111 = 1 1110 = 30
```
