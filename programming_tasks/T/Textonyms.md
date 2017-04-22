[1]: http://rosettacode.org/wiki/Textonyms

# [Textonyms][1]

```ruby
var words = ARGF.grep(/^[[:alpha:]]+\z/)
 
var dials = words.group_by {
    .tr('abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ',
        '2223334445556667777888999922233344455566677778889999')
}
 
var textonyms = dials.grep_v { .len > 1 }
 
say <<-"END"
    There are #{words.len} words which can be represented by the digit key mapping.
    They require #{dials.len} digit combinations to represent them.
    #{textonyms.len} digit combinations represent Textonyms.
    END
 
say "Top 5 in ambiguity:"
say textonyms.sort_by { |_,v| -v.len }.first(5).join("\n")
 
say "\nTop 5 in length:"
say textonyms.sort_by { |k,_| -k.len }.first(5).join("\n")
```

#### Output:
```
$ sidef textonyms.sf < unixdict.txt
There are 24978 words which can be represented by the digit key mapping.
They require 22903 digit combinations to represent them.
1473 digit combinations represent Textonyms.

Top 5 in ambiguity:
["729", ["paw", "pax", "pay", "paz", "raw", "ray", "saw", "sax", "say"]]
["269", ["amy", "any", "bmw", "bow", "box", "boy", "cow", "cox", "coy"]]
["2273", ["acre", "bard", "bare", "base", "cape", "card", "care", "case"]]
["726", ["pam", "pan", "ram", "ran", "sam", "san", "sao", "scm"]]
["782", ["pta", "pub", "puc", "pvc", "qua", "rub", "sub"]]

Top 5 in length:
["25287876746242", ["claustrophobia", "claustrophobic"]]
["7244967473642", ["schizophrenia", "schizophrenic"]]
["666628676342", ["onomatopoeia", "onomatopoeic"]]
["49376746242", ["hydrophobia", "hydrophobic"]]
["2668368466", ["contention", "convention"]]
```
