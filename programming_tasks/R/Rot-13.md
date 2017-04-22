[1]: http://rosettacode.org/wiki/Rot-13

# [Rot-13][1]

```ruby
# Returns a copy of 's' with rot13 encoding.
func rot13(s) {
    s.tr('A-Za-z', 'N-ZA-Mn-za-m')
}
 
# Perform rot13 on standard input.
STDIN.each { |line| say rot13(line) }
```
