[1]: http://rosettacode.org/wiki/Middle_three_digits

# [Middle three digits][1]

```ruby
func middle_three(n) {
  var l = n.len
  if (l < 3) {
    "#{n} is too short"
  } elsif (l.is_even) {
    "#{n} has an even number of digits"
  } else {
    "The three middle digits of #{n} are: " + n.digits.slice((l-3)/2).first(3).flip.join
  }
}

var nums = %n(
    123 12345 1234567 987654321 10001 -10001 -123 -100 100 -12345
    1 2 -1 -10 2002 -2002 0
)
nums.each { say middle_three(_) }
```

#### Output:
```
The three middle digits of 123 are: 123
The three middle digits of 12345 are: 234
The three middle digits of 1234567 are: 345
The three middle digits of 987654321 are: 654
The three middle digits of 10001 are: 000
The three middle digits of -10001 are: 000
The three middle digits of -123 are: 123
The three middle digits of -100 are: 100
The three middle digits of 100 are: 100
The three middle digits of -12345 are: 234
1 is too short
2 is too short
-1 is too short
-10 is too short
2002 has an even number of digits
-2002 has an even number of digits
0 is too short
```
