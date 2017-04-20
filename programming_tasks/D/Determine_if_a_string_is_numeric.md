[1]: http://rosettacode.org/wiki/Determine_if_a_string_is_numeric

# [Determine if a string is numeric][1]

There is the the _String.looks_like_number_ method, which returns true when a given strings looks like a number:

```ruby
say "0.1E-5".looks_like_number       #=> true
```


Alternatively, we can use regular expressions to determine this:

```ruby
func is_numeric(s) {
    (s ~~ /^[+-]?+(?=\.?[0-9])[0-9_]*+(?:\.[0-9_]++)?(?:[Ee](?:[+-]?+[0-9_]+))?\z/) ||
    (s ~~ /^0(?:b[10_]*|x[0-9A-Fa-f_]*|[0-9_]+\b)\z/)
}
```


Sample:

```ruby
var strings = %w(0 0.0 -123 abc 0x10 0xABC 123a -123e3 0.1E-5 50e);
for str in strings {
    say ("%9s => %s" % (str, is_numeric(str)))
}
```

#### Output:
```
        0 => true
      0.0 => true
     -123 => true
      abc => false
     0x10 => true
    0xABC => true
     123a => false
   -123e3 => true
   0.1E-5 => true
      50e => false
```
