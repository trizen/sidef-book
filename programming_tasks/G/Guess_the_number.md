[1]: https://rosettacode.org/wiki/Guess_the_number

# [Guess the number][1]

```ruby
var n = pick(1..10)
print 'Guess the number: '
while (n != read(Number).int) {
    print 'Wrong! Guess again: '
}
say 'Well guessed!'
```
