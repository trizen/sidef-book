[1]: https://rosettacode.org/wiki/Phrase_reversals

# [Phrase reversals][1]

```ruby
var str    = "rosetta code phrase reversal";
 
say str.reverse;                            # reversed string
say str.words.map{.reverse}.join(' ');      # words reversed
say str.words.reverse.join(' ');            # word order reversed
```

#### Output:
```
lasrever esarhp edoc attesor
attesor edoc esarhp lasrever
reversal phrase code rosetta
```