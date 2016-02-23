[1]: http://rosettacode.org/wiki/Kaprekar_numbers

# [Kaprekar numbers][1]

```ruby
var kap = Hash()
var nt = frequire('ntheory')
 
15.times { |n|
    var np = int(10**n)-1
    nt.fordivisors({ |d|
        var dp = np/d
        if (Math.gcd(d, dp).is_one) {
            kap{ dp.is_one ? d : d.invmod(dp)*d } := 0 ++
        }
    }, np)
}
 
var nums = kap.keys.map{.to_n}.sort
for n in range(6, 14) {
    var np = int(10**n)-1
    printf("Kaprekar numbers <= 10^%2d:  %5d\n", n, nums.count{ .le(np) })
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
