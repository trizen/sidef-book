[1]: http://rosettacode.org/wiki/99_Bottles_of_Beer

# [99 Bottles of Beer][1]

```ruby
for i in (100 ^.. 0) {
    var bottles = "#{i == 0 ? 'No' : i} bottle#{i == 1 ? '' : 's'}"
    var sentence = "#{bottles} of beer on the wall" -> say
    if (i > 0) {
        say sentence.substr(0, bottles.length + 8)
        say "Take one down, pass it around\n"
    }
}
```


*Simpler:*

```ruby
for n in (100 ^.. 2) {
  say "#{n} bottles of beer on the wall, #{n} bottles of beer!"
  say "Take one down, pass it around, #{n - 1} bottle#{n > 2 ? 's' : ''} of beer on the wall.\n"
}
 
say "One bottle of beer on the wall, one bottle of beer!"
say "Take one down, pass it around, no more bottles of beer on the wall."
```
