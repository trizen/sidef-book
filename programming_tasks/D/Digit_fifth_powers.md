[1]: https://rosettacode.org/wiki/Digit_fifth_powers

# [Digit fifth powers][1]

```ruby
func digit_nth_powers(n, base=10) {
 
    var D = @(^base)
    var P = D.map {|d| d**n }
    var A = []
    var m = (base-1)**n
 
    for(var (k, t) = (1, 1); k*m >= t; (++k, t*=base)) {
        D.combinations_with_repetition(k, {|*c|
            var v = c.sum {|d| P[d] }
            A.push(v) if (v.digits(base).sort == c)
        })
    }
 
    A.sort.grep { _ > 1 }
}
 
for n in (3..8) {
    var a = digit_nth_powers(n)
    say "Sum of #{n}-th powers of their digits: #{a.join(' + ')} = #{a.sum}"
}
```

#### Output:
```
Sum of 3-th powers of their digits: 153 + 370 + 371 + 407 = 1301
Sum of 4-th powers of their digits: 1634 + 8208 + 9474 = 19316
Sum of 5-th powers of their digits: 4150 + 4151 + 54748 + 92727 + 93084 + 194979 = 443839
Sum of 6-th powers of their digits: 548834 = 548834
Sum of 7-th powers of their digits: 1741725 + 4210818 + 9800817 + 9926315 + 14459929 = 40139604
Sum of 8-th powers of their digits: 24678050 + 24678051 + 88593477 = 137949578
```
