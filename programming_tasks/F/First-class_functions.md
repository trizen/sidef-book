[1]: https://rosettacode.org/wiki/First-class_functions

# [First-class functions][1]

```ruby
func compose(f,g) {
    func (*args) {
        f(g(args...))
    }
}

var cube  = func(a) { a.pow(3) }
var croot = func(a) { a.root(3) }

var flist1 = [Num.method(:sin),  Num.method(:cos),  cube]
var flist2 = [Num.method(:asin), Num.method(:acos), croot]

for a,b (flist1 ~Z flist2) {
    say compose(a, b)(0.5)
}
```

#### Output:
```
0.5
0.5
0.5
```
