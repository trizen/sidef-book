[1]: http://rosettacode.org/wiki/Zig-zag_matrix

# [Zig-zag matrix][1]

```ruby
func zig_zag(w, h) {
 
    var r = [];
    var n = 0;
 
    0 .. h-1 map { |e|
        0 .. w-1 map { |f|
            [e, f]
        }
    }
    -> reduce('+')
    -> sort { |a, b|
           (a[0]+a[1] <=> b[0]+b[1])
        || (a[0]+a[1] %% 2 ? a[0]<=>b[0]
                           : a[1]<=>b[1])
    }
    -> each { |a|
       r[a[1]][a[0]] = n++;
    };
 
    return r;
}
 
zig_zag(5, 5).each {.join('', {|i| "%4i" % i}).say};
```

#### Output:
```
   0   1   5   6  14
   2   4   7  13  15
   3   8  12  16  21
   9  11  17  20  22
  10  18  19  23  24
```