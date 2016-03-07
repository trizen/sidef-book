[1]: http://rosettacode.org/wiki/Random_numbers

# [Random numbers][1]

```ruby
var arr = 1000.of { 1 + (0.5 * (-2 * 1.rand.log -> sqrt) * (Number.tau * 1.rand -> cos)) }
arr.each { .say }
```
