[1]: http://rosettacode.org/wiki/Bulls_and_cows/Player

# [Bulls and cows/Player][1]

```ruby
# Build a list of all possible solutions.  The regular expression weeds
# out numbers containing zeroes or repeated digits.
var candidates = ('1234'..'9876' -> grep {|n| !(n =~ /0 | (\d) .*? \1 /x) }.map{.to_i.digits});
 
# Repeatedly prompt for input until the user supplies a reasonable score.
# The regex validates the user's input and then returns two numbers.
func read_score(guess) {
    loop {
        "My guess: %s   (from %d possibilities)\n"
            -> printf(guess.join, candidates.len);
 
        if (var m = (Sys.scanln("bulls cows: ") =~ /^\h*(\d)\h*(\d)\h*$/)) {
            var (bulls, cows) = m.cap.map{.to_i}...;
            bulls+cows <= 4 && return (bulls, cows);
        }
 
        say "Please specify the number of bulls and the number of cows";
    }
}
 
func score_correct(a, b, bulls, cows) {
    var (exact, loose) = (0, 0);
 
    3.range.each { |i|
        a[i] == b[i] ? ++exact
                     : (b.contains(a[i]) && ++loose)
    }
 
    (bulls == exact) && (cows == loose);
}
 
# Pick a number, display it, get the score, and discard candidates
# that don't match the score:
loop {
    var guess = candidates.pick;
    var (bulls, cows) = read_score(guess);
    candidates.grep!{|n| score_correct(n, guess, bulls, cows) };
    candidates.len > 1 || break;
}
 
# Print the secret number or the error message
say (
     candidates.len == 1 ? ("Your secret number is: %d" % candidates[0].join)
                         : ("I think you made a mistake with your scoring")
    )
```


*Output:*


#### Output:
```
My guess: 7432   (from 3024 possibilities)
bulls cows: 0 1
My guess: 9216   (from 720 possibilities)
bulls cows: 1 1
My guess: 6813   (from 128 possibilities)
bulls cows: 0 1
My guess: 9157   (from 24 possibilities)
bulls cows: 1 3
Your secret number is: 9571
```