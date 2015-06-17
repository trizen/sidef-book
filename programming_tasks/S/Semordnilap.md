[1]: http://rosettacode.org/wiki/Semordnilap

# [Semordnilap][1]

```ruby
var c = 0;
var seen = Hash.new(0);
 
ARGF.each { |line|
    line.chomp!;
    var r = line.reverse;
    ?seen[r]++ && (c++ < 5) && say "#{line} #{r}" || seen[line]++;
}
 
say c;    # => 158
```