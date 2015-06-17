[1]: http://rosettacode.org/wiki/String_matching

# [String matching][1]

```ruby
var first = "abc-abcdef-abcd";
var second = "abc";
 
say first.begins_with(second);      #=> true
say first.contains(second);         #=> true
say first.ends_with(second);        #=> false
 
# Get and print the location of the match
say first.index(second);            #=> 0
 
# Find multiple occurrences of a string
while (var(pos=-1) = first.index(second, pos+1) != -1) {
    say "Match at pos: #{pos}";
}
```