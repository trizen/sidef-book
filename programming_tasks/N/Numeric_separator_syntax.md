[1]: https://rosettacode.org/wiki/Numeric_separator_syntax

# [Numeric separator syntax][1]

Sidef allows underscores as a separator character in numeric inputs.

```ruby
# Int
say 1_2_3;  # 123
 
# Binary Int
say 0b1_0_1_0_1; # 21
 
# Hexadecimal Int
say 0xa_bc_d; # 43981
 
# Rational
say 1_2_3_4.2_5; # 1234.25
 
# Rational in exponential notation
say 6.0_22e4; # 60220
 
# Apart from starting the number with an underscore, can be placed anywhere in the number.
 
say 1234_.25;       # 1234.25
say 1234._25;       # 1234.25
say 1234.25_;       # 1234.25
say 12__34.25;      # 1234.25
# say _1234.25;     # syntax error
```
