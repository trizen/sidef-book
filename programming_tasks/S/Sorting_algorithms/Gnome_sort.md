[1]: http://rosettacode.org/wiki/Sorting_algorithms/Gnome_sort

# [Sorting algorithms/Gnome sort][1]

```ruby
class Array {
    method gnomesort {
        var (i=1, j=2);
        var len = self.len;
        while (i < len) {
            if (self[i-1] <= self[i]) {
                [j, j+1] » (\i, \j);
            }
            else {
                [self[i], self[i-1]] » (\self[i-1], \self[i]);
                if (--i == 0) {
                    [j, j+1] » (\i, \j);
                }
            }
        };
        return self;
    }
}
 
var ary = [7,6,5,9,8,4,3,1,2,0];
say ary.gnomesort.dump;
```

#### Output:
```
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
```