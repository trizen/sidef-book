[1]: http://rosettacode.org/wiki/9_billion_names_of_God_the_integer

# [9 billion names of God the integer][1]

```ruby
var cache = [[1]];
 
func cumu (n) {
    cache.len ... n -> each { |l|
        var r = [0]
        l.times { |i|
            r.append(r[-1] + cache[l-i][[i, l-i].min])
        }
        cache.append(r)
    }
    cache[n]
}
 
func row (n) {
    var r = cumu(n);
    n.of {|i| r[i] - r[i-1] }
}
 
say "rows:";
15.times { |i|
    "%2d: %s\n".printf(i, row(i))
}
 
say "\nsums:";
 
[23, 123, 1234, 12345].each { |i|
    "%2d : %4d\n".printf(i, cumu(i)[-1])
}
```

#### Output:
```
rows:
 1: [1]
 2: [1, 1]
 3: [1, 1, 1]
 4: [1, 2, 1, 1]
 5: [1, 2, 2, 1, 1]
 6: [1, 3, 3, 2, 1, 1]
 7: [1, 3, 4, 3, 2, 1, 1]
 8: [1, 4, 5, 5, 3, 2, 1, 1]
 9: [1, 4, 7, 6, 5, 3, 2, 1, 1]
10: [1, 5, 8, 9, 7, 5, 3, 2, 1, 1]
11: [1, 5, 10, 11, 10, 7, 5, 3, 2, 1, 1]
12: [1, 6, 12, 15, 13, 11, 7, 5, 3, 2, 1, 1]
13: [1, 6, 14, 18, 18, 14, 11, 7, 5, 3, 2, 1, 1]
14: [1, 7, 16, 23, 23, 20, 15, 11, 7, 5, 3, 2, 1, 1]
15: [1, 7, 19, 27, 30, 26, 21, 15, 11, 7, 5, 3, 2, 1, 1]

sums:
23 : 1255
123 : 2552338241
1234 : 156978797223733228787865722354959930
^C
```