[1]: http://rosettacode.org/wiki/Pointers_and_references

# [Pointers and references][1]

A simple example of passing a variable-reference to a function:

```ruby
func assign2ref(ref, value) {
    *ref = value;
}
 
var x = 10;
assign2ref(\x, 20);
say x;      # x is now 20
```