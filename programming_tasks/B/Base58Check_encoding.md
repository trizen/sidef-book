[1]: https://rosettacode.org/wiki/Base58Check_encoding

# [Base58Check encoding][1]

```ruby
func encode_base58(n) {
    static chars = %w(
        1 2 3 4 5 6 7 8 9
        A B C D E F G H   J K L M N   P Q R S T U V W X Y Z
        a b c d e f g h i j k   m n o p q r s t u v w x y z
    )
    [chars[n.polymod(n.ilog(58).of(58)...)]].join.flip
}
 
var tests = [
    [25420294593250030202636073700053352635053786165627414518, "6UwLL9Risc3QfPqBUvKofHmBQ7wMtjvM"],
    [97, "2g"],[6447714, "a3gV"],[6513507, "aPEr"],
    [658885050385564465925592505944209249682185612903, "2cFupjhnEsSn59qHXstmK2ffpLv2"],
    [349694840079, "ABnLTmg"], [3529059230209907258589, "3SEo3LWLoPntC"],
    [1462650772, "3EFU7m"], [1117661258925082241147681, "EJDM8drfXA6uyA"], [281563422, "Rt5zm"]
]
 
for num, enc in (tests) {
    printf("%56s -> %s\n", num, encode_base58(num))
    assert_eq(encode_base58(num), enc)
}
```

#### Output:
```
25420294593250030202636073700053352635053786165627414518 -> 6UwLL9Risc3QfPqBUvKofHmBQ7wMtjvM
                                                      97 -> 2g
                                                 6447714 -> a3gV
                                                 6513507 -> aPEr
        658885050385564465925592505944209249682185612903 -> 2cFupjhnEsSn59qHXstmK2ffpLv2
                                            349694840079 -> ABnLTmg
                                  3529059230209907258589 -> 3SEo3LWLoPntC
                                              1462650772 -> 3EFU7m
                               1117661258925082241147681 -> EJDM8drfXA6uyA
                                               281563422 -> Rt5zm
```
