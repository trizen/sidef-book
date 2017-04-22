[1]: http://rosettacode.org/wiki/Random_numbers

# [Random numbers][1]

```ruby
var arr = 1000.of { 1 + (0.5 * sqrt(-2 * 1.rand.log) * cos(Num.tau * 1.rand)) }
arr.each { .say }
```
