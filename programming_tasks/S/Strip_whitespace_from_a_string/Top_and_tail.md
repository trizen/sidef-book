[1]: http://rosettacode.org/wiki/Strip_whitespace_from_a_string/Top_and_tail

# [Strip whitespace from a string/Top and tail][1]

```ruby
var s = " \t\v\r\n\ffoo bar \t\v\r\n\f";
say s.strip_beg.dump;    # remove leading whitespaces
say s.strip_end.dump;    # remove trailing whitespaces
say s.strip.dump;        # remove both leading and trailing whitespace
```

#### Output:
```
"foo bar \t\13\r\n\f"
" \t\13\r\n\ffoo bar"
"foo bar"
```