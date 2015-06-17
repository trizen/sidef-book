[1]: http://rosettacode.org/wiki/Strip_a_set_of_characters_from_a_string

# [Strip a set of characters from a string][1]

```ruby
func stripchars(str, char_list) {
    str.tr(char_list, "", "d");
};
```


or:

```ruby
func stripchars(str, char_list) {
    str.split(1).grep {|c| !char_list.contains(c)}.join;
};
```


Calling the function:

```ruby
say stripchars("She was a soul stripper. She took my heart!", "aei");
```

#### Output:
```
Sh ws  soul strppr. Sh took my hrt!
```