[1]: http://rosettacode.org/wiki/Kaprekar_numbers

# [Kaprekar numbers][1]

```ruby
var kapr = Set()

for n in (1..15) {
    var k = (10**n - 1)
    k.udivisors.each {|d|
        var dp = k/d
        kapr << (dp == 1 ? d : d*invmod(d, dp))
    }
}

say kapr.grep { .<= 1e4 }.sort

for n in (6 .. 14) {
    var k = (10**n - 1)
    printf("Kaprekar numbers <= 10^%2d:  %5d\n", n, kapr.count_by { .<= k })
}
```

#### Output:
```
[1, 9, 45, 55, 99, 297, 703, 999, 2223, 2728, 4879, 4950, 5050, 5292, 7272, 7777, 9999]
Kaprekar numbers <= 10^ 6:     54
Kaprekar numbers <= 10^ 7:     62
Kaprekar numbers <= 10^ 8:     91
Kaprekar numbers <= 10^ 9:    102
Kaprekar numbers <= 10^10:    132
Kaprekar numbers <= 10^11:    149
Kaprekar numbers <= 10^12:    264
Kaprekar numbers <= 10^13:    281
Kaprekar numbers <= 10^14:    316
```
