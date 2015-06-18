[1]: http://rosettacode.org/wiki/Semordnilap

# [Semordnilap][1]

```ruby
var c = 0;
var seen = Hash.new;
seen.default(0);

ARGF.each { |line|
    line.chomp!;
    var r = line.reverse;
    (seen[r]++ && (c++ < 5) && say "#{line} #{r}") || seen[line]++;
}

say c;
```

#### Output:
```
$ sidef semordnilap.sf < unixdict.txt
ca ac
dab bad
diva avid
dna and
drab bard
158
```
