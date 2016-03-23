# break

The `break` statement is used to exit early from loops.

```ruby
var set_of_numbers = 0..100

for n in set_of_numbers {
    if is_prime(n) {
        say "Set contains a prime number: #{n}"
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
