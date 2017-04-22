[1]: http://rosettacode.org/wiki/Stern-Brocot_sequence

# [Stern-Brocot sequence][1]

```ruby
# Declare a function to generate the Stern-Brocot sequence
func stern_brocot {
    var list = [1, 1]
    func {
        list.append(list[0]+list[1], list[1])
        list.shift
    }
}
 
# Show the first fifteen members of the sequence.
say 15.of(stern_brocot()).join(' ')
 
# Show the (1-based) index of where the numbers 1-to-10 first appears
# in the sequence, and where the number 100 first appears in the sequence.
for i (1..10, 100) {
    var index = 1
    var generator = stern_brocot()
    while (generator() != i) {
        ++index
    }
    say "First occurrence of #{i} is at index #{index}"
}
 
# Check that the greatest common divisor of all the two consecutive
# members of the series up to the 1000th member, is always one.
var generator = stern_brocot()
var (a, b) = (generator(), generator())
{
    assert_eq(gcd(a, b), 1)
    a = b
    b = generator()
} * 1000
 
say "All GCD's are 1"
```

#### Output:
```
1 1 2 1 3 2 3 1 4 3 5 2 5 3 4
First occurrence of 1 is at index 1
First occurrence of 2 is at index 3
First occurrence of 3 is at index 5
First occurrence of 4 is at index 9
First occurrence of 5 is at index 11
First occurrence of 6 is at index 33
First occurrence of 7 is at index 19
First occurrence of 8 is at index 21
First occurrence of 9 is at index 35
First occurrence of 10 is at index 39
First occurrence of 100 is at index 1179
All GCD's are 1
```
