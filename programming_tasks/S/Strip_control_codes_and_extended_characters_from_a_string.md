[1]: http://rosettacode.org/wiki/Strip_control_codes_and_extended_characters_from_a_string

# [Strip control codes and extended characters from a string][1]

```ruby
var str = "\ba\x00b\n\rc\fd\xc3\x7ffoo";
 
var letters = str.chars»ord»();
say letters»chr»().join.dump;
 
var nocontrols = letters.grep{ (_ > 32) && (_ != 127) };
say nocontrols»chr»().join.dump;
 
var noextended = nocontrols.grep{ _ < 127 };
say noextended»chr»().join.dump;
```

#### Output:
```
"\ba\0b\n\rc\fd\xC3\x7Ffoo"
"abcd\xC3foo"
"abcdfoo"
```