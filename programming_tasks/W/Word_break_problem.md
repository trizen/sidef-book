[1]: https://rosettacode.org/wiki/Word_break_problem

# [Word break problem][1]

```ruby
func word_break (str, words) {
 
    var r = ->(str, arr=[]) {
        return true if str.is_empty
        for word in (words) {
            str.begins_with(word) || next
            if (__FUNC__(str.substr(word.len), arr)) {
                arr << word
                return arr
            }
        }
        return false
    }(str)
 
    r.kind_of(Array) ? r.reverse : nil
}
 
var words = %w(a o is pi ion par per sip miss able)
var strs = %w(a amiss parable opera operable inoperable permission mississippi)
 
for str in (strs) {
   printf("%11s: %s\n", str, word_break(str, words) \\ '(not possible)')
}
```

#### Output:
```
          a: ["a"]
      amiss: ["a", "miss"]
    parable: ["par", "able"]
      opera: ["o", "per", "a"]
   operable: ["o", "per", "able"]
 inoperable: (not possible)
 permission: ["per", "miss", "ion"]
mississippi: ["miss", "is", "sip", "pi"]
```
