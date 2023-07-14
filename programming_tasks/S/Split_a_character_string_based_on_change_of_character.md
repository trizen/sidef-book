[1]: https://rosettacode.org/wiki/Split_a_character_string_based_on_change_of_character

# [Split a character string based on change of character][1]

```ruby
func group(str) {
    gather {
        while (var match = (str =~ /((.)\g{-1}*)/g)) {
            take(match[0])
        }
    }
}
 
say group(ARGV[0] \\ 'gHHH5YY++///\\').join(', ')
```

#### Output:
```
g, HHH, 5, YY, ++, ///, \
```