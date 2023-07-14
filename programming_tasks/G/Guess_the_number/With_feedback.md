[1]: https://rosettacode.org/wiki/Guess_the_number/With_feedback

# [Guess the number/With feedback][1]

```ruby
var number = pick(1..10)
say "Guess the number between 1 and 10"
 
loop {
    given(var n = read("> ", Number).to_i) {
        when (number)     { say "You guessed it."; break }
        case (n < number) { say "Too low" }
        default           { say "Too high" }
    }
}
```
