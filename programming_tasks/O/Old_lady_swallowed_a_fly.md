[1]: https://rosettacode.org/wiki/Old_lady_swallowed_a_fly

# [Old lady swallowed a fly][1]

```ruby
var victims = [
    :fly:    "  I don't know why S—",
    :spider: "  That wriggled and jiggled and tickled inside her.",
    :bird:   "  How absurd, T!",
    :cat:    "  Fancy that, S!",
    :dog:    "  What a hog, T!",
    :goat:   "  She just opened her throat, and in walked the goat!",
    :cow:    "  I don't know how S!",
    :horse:  "  She's dead, of course...",
]
 
var history = ["I guess she'll die...\n"];
 
for victim,verse in victims {
    say "There was an old lady who swallowed a #{victim}...";
 
    verse.sub!(/\bS\b/, "she swallowed the #{victim}");
    verse.sub!(/\bT\b/, "to swallow a #{victim}!");
 
    say verse;
    verse ~~ /dead/ && break;
 
    history[0].sub!(/^X/, "She swallowed the #{victim}");
    history.each{.say};
    history.len < 5 && history.unshift(verse);
    history.unshift("X to catch the #{victim},");
}
```
