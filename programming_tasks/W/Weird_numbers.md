[1]: https://rosettacode.org/wiki/Weird_numbers

# [Weird numbers][1]

```ruby
func is_pseudoperfect(n, d = n.divisors.slice(0, -2), s = d.sum, m = d.end) {
 
    return false if (m < 0)
 
    while (d[m] > n) {
        s -= d[m--]
    }
 
    return true if (n == s)
    return true if (d[m] == n)
 
    __FUNC__(n-d[m], d, s-d[m], m-1) || __FUNC__(n, d, s-d[m], m-1)
}
 
func is_weird(n) {
    (n.sigma > 2*n) && !is_pseudoperfect(n)
}
 
var w = (1..Inf -> lazy.grep(is_weird).first(25))
say "The first 25 weird numbers:\n#{w.join(' ')}"
```

#### Output:
```
The first 25 weird numbers:
70 836 4030 5830 7192 7912 9272 10430 10570 10792 10990 11410 11690 12110 12530 12670 13370 13510 13790 13930 14770 15610 15890 16030 16310
```