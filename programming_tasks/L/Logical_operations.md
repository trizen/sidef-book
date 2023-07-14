[1]: https://rosettacode.org/wiki/Logical_operations

# [Logical operations][1]

```ruby
func logic(a, b) {
    say ("a and b: ", a && b);
    say ("a  or b: ", a || b);
    say ("a xor b: ", a ^ b);
    say ("  not a: ", !a);
}
 
logic(false, true);
```

#### Output:
```
a and b: false
a  or b: true
a xor b: true
  not a: true
```