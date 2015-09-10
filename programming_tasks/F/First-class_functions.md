[1]: http://rosettacode.org/wiki/First-class_functions

# [First-class functions][1]

```ruby
func compose(f,g) {
    closure { |*args|
        f(g(args...));
    }
}
 
var cube  = func(a) { a.pow(3) };
var croot = func(a) { a.root(3) };
 
var flist1 = [Math.method(:sin), Math.method(:cos), cube];
var flist2 = [Math.method(:asin), Math.method(:acos), croot];
 
flist1.range.each { |i|
    say compose(flist1[i], flist2[i])(0.5);
}
```

#### Output:
```
0.5
0.499999999999998
0.5
```