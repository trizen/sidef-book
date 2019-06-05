[1]: https://rosettacode.org/wiki/Chernick's_Carmichael_numbers

# [Chernick's Carmichael numbers][1]

```ruby
func chernick_carmichael_factors (n, m) {
    [6*m + 1, 12*m + 1, {|i| 2**i * 9*m + 1 }.map(1 .. n-2)...]
}
 
func is_chernick_carmichael (n, m) {
    (n == 2) ? (is_prime(6*m + 1) && is_prime(12*m + 1))
             : (is_prime(2**(n-2) * 9*m + 1) && __FUNC__(n-1, m))
}
 
func chernick_carmichael_number(n, callback) {
    var multiplier = (n>4 ? 2**(n-4) : 1)
    var m = (1..Inf -> first {|m| is_chernick_carmichael(n, m * multiplier) })
    var f = chernick_carmichael_factors(n, m * multiplier)
    callback(f...)
}
 
for n in (3..9) {
    chernick_carmichael_number(n, {|*f| say "a(#{n}) = #{f.join(' * ')}" })
}
```

#### Output:
```
a(3) = 7 * 13 * 19
a(4) = 7 * 13 * 19 * 37
a(5) = 2281 * 4561 * 6841 * 13681 * 27361
a(6) = 2281 * 4561 * 6841 * 13681 * 27361 * 54721
a(7) = 4681921 * 9363841 * 14045761 * 28091521 * 56183041 * 112366081 * 224732161
a(8) = 5703361 * 11406721 * 17110081 * 34220161 * 68440321 * 136880641 * 273761281 * 547522561
a(9) = 5703361 * 11406721 * 17110081 * 34220161 * 68440321 * 136880641 * 273761281 * 547522561 * 1095045121
```
