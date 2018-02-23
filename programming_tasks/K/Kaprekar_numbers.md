[1]: http://rosettacode.org/wiki/Kaprekar_numbers

# [Kaprekar numbers][1]

```ruby
var kap = Hash()

for n in (1..15) {
    var np = (10**n - 1)
    for d in (np.divisors) {
        var dp = np/d
        if (is_coprime(dp, d)) {
            kap{ dp == 1 ? d : d*invmod(d, dp) } := 0 ++
        }
    }
}

var nums = kap.keys.map{ Num(_) }.sort

for n in (6 .. 14) {
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
