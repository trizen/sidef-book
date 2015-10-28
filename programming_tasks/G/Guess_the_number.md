[1]: http://rosettacode.org/wiki/Guess_the_number

# [Guess the number][1]

```ruby
var n = 10.rand(1).int;
print 'Guess the number: ';
while (n != read(Number).int) {
    print 'Wrong! Guess again: '
}
say 'Well guessed!';
```