[1]: http://rosettacode.org/wiki/Digital_root/Multiplicative_digital_root

# [Digital root/Multiplicative digital root][1]

```ruby
func mdroot(n) {
  var (mdr, persist) = (n, 0)
  while (mdr >= 10) {
    mdr = mdr.digits.product
    ++persist
  }
  [mdr, persist]
}
 
say "Number: MDR  MP\n======  ===  =="
[123321, 7739, 893, 899998].each{|n| "%6d: %3d %3d\n"
                           .printf(n, mdroot(n)...) }
 
var counter = Hash()
 
Inf.times { |i|
  var j = i-1
  counter{mdroot(j).first} := [] << j
  break if counter.values.all {|v| v.len >= 5 }
}
 
say "\nMDR: [n0..n4]\n===  ========"
10.times {|i| "%3d: %s\n".printf(i-1, counter{i-1}.first(5)) }
```

#### Output:
```
Number: MDR  MP
======  ===  ==
123321:   8   3
  7739:   8   3
   893:   2   3
899998:   0   2

MDR: [n0..n4]
===  ========
  0: [0, 10, 20, 25, 30]
  1: [1, 11, 111, 1111, 11111]
  2: [2, 12, 21, 26, 34]
  3: [3, 13, 31, 113, 131]
  4: [4, 14, 22, 27, 39]
  5: [5, 15, 35, 51, 53]
  6: [6, 16, 23, 28, 32]
  7: [7, 17, 71, 117, 171]
  8: [8, 18, 24, 29, 36]
  9: [9, 19, 33, 91, 119]
```