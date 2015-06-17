[1]: http://rosettacode.org/wiki/Sort_using_a_custom_comparator

# [Sort using a custom comparator][1]

```ruby
func mycmp(a, b) { (b.len <=> a.len) || (a.lc <=> b.lc) };
var strings = %w(Here are some sample strings to be sorted);
var sorted = strings.sort(mycmp);
```