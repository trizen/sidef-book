[1]: https://rosettacode.org/wiki/Rosetta_Code/Count_examples

# [Rosetta Code/Count examples][1]

```ruby
var lwp = require('LWP::UserAgent').new(agent => 'Mozilla/5.0');
 
var site = 'https://rosettacode.org';
var list_url = '/mw/api.php?action=query&list=categorymembers&'+
               'cmtitle=Category:Programming_Tasks&cmlimit=500&format=xml';
 
var content = lwp.get(site + list_url).decoded_content;
 
while (var m = content.match(/cm.*?title="(.*?)"/g)) {
    (var slug = m[0]).gsub!(' ', '_');
    var count = lwp.get("#{site}/wiki/#{slug}").decoded_content.count(/toclevel-1/g);
    say "#{m[0]}: #{count} examples";
}
```

#### Output:
```
100 doors: 2180 examples
24 game: 760 examples
24 game/Solve: 450 examples
9 billion names of God the integer: 320 examples
99 Bottles of Beer: 2330 examples
A+B: 1800 examples
ABC Problem: 720 examples
Abstract type: 680 examples
...
```