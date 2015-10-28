[1]: http://rosettacode.org/wiki/Bulls_and_cows

# [Bulls and cows][1]

```ruby
var size = 4;
var num = (1..9 -> shuffle.first(size));
 
for (var guesses = 1; true; guesses++) {
 
    var bulls = 0;
    var cows  = 0;
 
    var input = Sys.scanln("Input: ").split(1)
                                     .unique
                                     .grep {.~~/^[1-9]$/}
                                     .map  {.to_i};
 
    input.len == size || (
        warn "Invalid input!\n"
        guesses--;
        next;
    );
 
    if (input == num) {
        printf("You did it in %d attempts!\n", guesses);
        break;
    }
 
    num.range.each { |i|
        if (num[i] == input[i]) {
            bulls++;
        }
        elsif (num.contains(input[i])) {
            cows++;
        }
    }
 
    "Bulls: %d; Cows: %d\n".printf(bulls, cows);
}
```

#### Output:
```
Input: 2953
Bulls: 1; Cows: 1
Input: 9654
Bulls: 1; Cows: 1
Input: 8924
Bulls: 1; Cows: 3
Input: 2894
You did it in 4 attempts!
```