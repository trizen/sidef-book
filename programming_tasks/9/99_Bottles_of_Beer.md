[1]: http://rosettacode.org/wiki/99_Bottles_of_Beer

# [99 Bottles of Beer][1]

```ruby
99.downto(0).each { |i|
    var bottles = "#{i == 0 ? 'No' : i} bottle#{i == 1 ? '' : 's'}";
    var sentence = "#{bottles} of beer on the wall" -> say;
    i > 0 && (
        sentence.substr(0, bottles.length + 8).say;
        "Take one down, pass it around\n".say;
    );
};
```


*Simpler:*

```ruby
99.downto(2).each { | n |
  say "#{n} bottles of beer on the wall, #{n} bottles of beer!";
  say "Take one down, pass it around, #{n - 1} bottle#{n > 2 ? 's' : ''} of beer on the wall.\n";
};
 
say "One bottle of beer on the wall, one bottle of beer!";
say "Take one down, pass it around, no more bottles of beer on the wall.";
```