[1]: https://rosettacode.org/wiki/Decimal_floating_point_number_to_binary

# [Decimal floating point number to binary][1]

```ruby
func dec2bin(String n) {
    Num(Num(n, 10).base(2), 10)
}
 
func bin2dec(String n) {
    Num(Num(n, 10).base(10), 2)
}
 
with("23.34375")   { |s| say ("  #{s} => ", dec2bin(s)) }
with("1011.11101") { |s| say (  "#{s} => ", bin2dec(s)) }
```

#### Output:
```
  23.34375 => 10111.01011
1011.11101 => 11.90625
```