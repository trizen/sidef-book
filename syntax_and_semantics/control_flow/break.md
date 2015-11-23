# break

The `break` statement is used to exit early from loops.

```ruby
for n in set_of_numbers {
    if isprime(n) {
        say "Set contains a prime number"
        break
    }
    else {
        say "Set did not contain any prime numbers"
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
