[1]: https://rosettacode.org/wiki/Pangram_checker

# [Pangram checker][1]

```ruby
define Eng = 'a'..'z'
define Hex = 'a'..'f'
define Cyr = %w(а б в г д е ж з и й к л м н о п р с т у ф х ц ч ш щ ъ ы ь э ю я ё)
 
func pangram(str, alpha=Eng) {
    var lstr = str.lc
    alpha.all {|c| lstr.contains(c) }
}
 
say pangram("The quick brown fox jumps over the lazy dog.")
say pangram("My dog has fleas.")
say pangram("My dog has fleas.", Hex)
say pangram("My dog backs fleas.", Hex)
say pangram("Съешь же ещё этих мягких французских булок, да выпей чаю", Cyr)
```

#### Output:
```
true
false
false
true
true
```
