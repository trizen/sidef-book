[1]: https://rosettacode.org/wiki/Mad_Libs

# [Mad Libs][1]

```ruby
var story = ARGF.slurp;
 
var blanks = Hash.new;
while (var m = /<(.*?)>/.gmatch(story)) {
    blanks.append(m[0]);
}
 
blanks.keys.sort.each { |blank|
    var replacement = Sys.scanln("#{blank}: ");
    blanks{blank} = replacement;
}
 
print story.gsub(/<(.*?)>/, {|s1| blanks{s1} });
```