[1]: https://rosettacode.org/wiki/Non-decimal_radices/Input

# [Non-decimal radices/Input][1]

```ruby
var dec            = '0123459';
var hex_noprefix   = 'abcf123';
var hex_withprefix = '0xabcf123';
var oct_noprefix   = '7651';
var oct_withprefix = '07651';
var bin_noprefix   = '101011001';
var bin_withprefix = '0b101011001';
 
say dec.num;                    # => 123459
say hex_noprefix.hex;           # => 180154659
say hex_withprefix.hex;         # => 180154659
say oct_noprefix.oct;           # => 4009
say oct_withprefix.oct;         # => 4009
say bin_noprefix.bin;           # => 345
say bin_withprefix.bin;         # => 345
```