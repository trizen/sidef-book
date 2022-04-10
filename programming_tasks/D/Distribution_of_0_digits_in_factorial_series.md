[1]: https://rosettacode.org/wiki/Distribution_of_0_digits_in_factorial_series

# [Distribution of 0 digits in factorial series][1]

```ruby
func mean_factorial_digits(n, d = 0) {
 
    var v = 1
    var total = 0.float
 
    for k in (1..n) {
        v *= k
        total += v.digits.count(d)/v.len
    }
 
    total / n
}
 
say mean_factorial_digits(100)
say mean_factorial_digits(1000)
say mean_factorial_digits(10000)
```

#### Output:
```
0.246753186167432217778415887197352699112940703327
0.203544551103164635640043803171145530298574116789
0.173003848241866053180036642893070615681027880906
```
