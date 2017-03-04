# break

The `break` statement is used to exit early from loops.

```ruby
for n in (1..100) {
    if (n.divisors.sum == 2*n) {
        say "#{n} is the first perfect number"
        break
    }
}
```

The statement can be used in any form of loops, including `while` and conditional `for` loops.

```ruby
var i = 0
while (true) {
    if (i >= 10) { break }
    say ++i
}
```
