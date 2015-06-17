[1]: http://rosettacode.org/wiki/Entropy

# [Entropy][1]

```ruby
func entropy(s) {
  var counts = Hash.new(0);
  s.each { |c| counts[c]++ };
  var len = s.len;
  [0, counts.values.map {|count| 
    var freq = count/len; freq * freq.log2 }...
  ]«-»;
}
 
say entropy("1223334444");
```

#### Output:
```
1.846439344671015493434197746305045223237
```