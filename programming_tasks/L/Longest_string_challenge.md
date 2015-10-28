[1]: http://rosettacode.org/wiki/Longest_string_challenge

# [Longest string challenge][1]

```ruby
var l = '';  # Sample longest string seen.
var a = '';  # Accumulator to save longest strings.
 
STDIN.each { |n|
    n.substr(l.len) ? (a = n; l = n)
                    : (!l.substr(n.len) && a.concat!(n));
}
 
print a;
```