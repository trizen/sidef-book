[1]: http://rosettacode.org/wiki/Quickselect_algorithm

# [Quickselect algorithm][1]

```ruby
func quickselect(a, k) {
    var pivot = a.pick;
    var left  = a.grep{|i| i < pivot};
    var right = a.grep{|i| i > pivot};
 
    given(var l = left.len) {
        when(k)     { pivot }
        case(k < l) { __FUNC__(left, k) }
        default     { __FUNC__(right, k - l - 1) }
    }
}
 
var v = [9, 8, 7, 6, 5, 0, 1, 2, 3, 4];
say v.range.map{|i| quickselect(v, i)};
```

#### Output:
```
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
```
