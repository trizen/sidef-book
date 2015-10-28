[1]: http://rosettacode.org/wiki/24_game

# [24 game][1]

```ruby
const digits  = (1..9 -> pick(4));
const grammar = Regex.new(
    '^ (?&exp) \z
      (?(DEFINE)
          (?<exp> ( (?&term) (?&op) (?&term) )+ )
          (?<term> \( (?&exp) \) | [' + digits.join + '])
          (?<op> [-+*/] )
      )', 'x'
);
 
say "Here are your digits: #{digits.join(' ')}";
 
loop {
    var input = Sys.scanln("Expression: ");
 
    var expr = input;
    expr -= /\s+/g;    # remove all whitespace
 
    input == 'q' && (
        say "Goodbye.  Sorry you couldn't win.";
        break;
    );
 
    var given_digits = digits.map{.to_s}.sort.join;
    var entry_digits = input.scan(/\d/).sort.join;
 
    if ((given_digits != entry_digits) || (expr !~ grammar)) {
        say "That's not valid";
        next;
    }
 
    given(var n = eval(input)) {
        when (24) { say "You win!"; break }
        default   { say "Sorry, your expression is #{n}, not 24" }
    }
}
```

#### Output:
```
Here are your digits: 8 2 3 4
Expression: 8 * (2 - (3 + 4))    
Sorry, your expression is -40, not 24
Expression: 8 * (2 - (3 -            
That's not valid
Expression: 8 * (2 - (3 - 4))
You win!
```