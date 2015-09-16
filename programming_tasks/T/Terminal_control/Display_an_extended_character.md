[1]: http://rosettacode.org/wiki/Terminal_control/Display_an_extended_character

# [Terminal control/Display an extended character][1]

```ruby
say '￡';
say "\x{FFE1}";
say "\N{FULLWIDTH POUND SIGN}";
say 0xffe1.chr;
```