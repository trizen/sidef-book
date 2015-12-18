[1]: http://rosettacode.org/wiki/Number_reversal_game

# [Number reversal game][1]

```ruby
var turn = 0;
var jumble = (1..9 -> bshuffle);        # best-shuffle
 
for (turn; jumble != 1..9; ++turn) {
    printf("%2d: %s - Flip how many digits ? ", turn, jumble.join(' '));
    var d = read(Number);
    jumble.@[0 .. d-1] = [jumble.@[0 .. d-1]].reverse...;
}
 
print "    #{jumble.join(' ')}\n";
print "You won in #{turn} turns.\n";
```