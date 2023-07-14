[1]: https://rosettacode.org/wiki/Find_palindromic_numbers_in_both_binary_and_ternary_bases

# [Find palindromic numbers in both binary and ternary bases][1]

```ruby
var format = "%11s %24s %38s\n"
format.printf("decimal", "ternary", "binary")
format.printf(0, 0, 0)
 
for n in (0 .. 2e5) {
    var pal = n.base(3)||''
    var b3 = (pal + '1' + pal.flip)
    var b2 = Num(b3, 3).base(2)
    if (b2 == b2.flip) {
        format.printf(Num(b2, 2), b3, b2)
    }
}
```

#### Output:
```
    decimal                  ternary                                 binary
          0                        0                                      0
          1                        1                                      1
       6643                100010001                          1100111110011
    1422773            2200021200022                  101011011010110110101
    5415589          101012010210101                10100101010001010100101
90396755477  22122022220102222022122  1010100001100000100010000011000010101
```