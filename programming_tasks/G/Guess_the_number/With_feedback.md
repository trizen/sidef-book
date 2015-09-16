[1]: http://rosettacode.org/wiki/Guess_the_number/With_feedback

# [Guess the number/With feedback][1]

```ruby
var number = rand(1..10);
say "Guess the number between 1 and 10";
 
loop {
    given(read(Number).int)
        > number           { say "You guessed it."; break }
        ~ range(1, number) { say "Too low" }
        :                  { say "Too high" }
    ;
}
```