[1]: http://rosettacode.org/wiki/Kaprekar_numbers

# [Kaprekar numbers][1]

```ruby
require('ntheory')
var kap = Hash()

for n (1..15) {
    var np = (10**n - 1)
    %S<ntheory>.fordivisors({ |d|
        var dp = np//d
        if ((d `gcd` dp) == 1) {
            kap{ dp == 1 ? d : d*invmod(d, dp) } := 0 ++
        }
    }, np)
}

var nums = kap.keys.map{.to_n}.sort

for n (6 .. 14) {
    var np = (10**n - 1)
    printf("Kaprekar numbers <= 10^%2d:  %5d\n", n, nums.count_by { .<= np })
}
```

#### Output:
```
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
