[1]: http://rosettacode.org/wiki/Sorting_algorithms/Strand_sort

# [Sorting algorithms/Strand sort][1]

```ruby
func merge(x, y) {
    var out = [];
    while (x && y) {
        given (x[-1] <=> y[-1])
            >  1 { out.prepend(x.pop) }
            > -1 { out.prepend(y.pop) }
            :    { out.prepend(x.pop, y.pop) }
    };
    x + y + out;
}
 
func strand(x) {
    x || return [];
    var out = [x.shift];
    if (x.len) {
        range(-x.len, -1).each { |i|
            if (x[i] >= out[-1]) {
                out.append(x.pop_at(i));
            }
        }
    };
    out;
}
 
func strand_sort(x) {
    var out = [];
    while (var strd = strand(x)) {
        out = merge(out, strd);
    };
    out;
}
 
var a = 10.of {100.rand.int};
say "Before: #{a}";
say "After: #{strand_sort(a.copy)}";
```

#### Output:
```
Before: 24 62 29 95 11 21 46 3 23 20
After: 3 11 20 21 23 24 29 46 62 95
```