[1]: https://rosettacode.org/wiki/Short-circuit_evaluation

# [Short-circuit evaluation][1]

```ruby
func a(bool) { print 'A'; return bool }
func b(bool) { print 'B'; return bool }
 
# Test-driver
func test() {
    for op in ['&&', '||'] {
        for x,y in [[1,1],[1,0],[0,1],[0,0]] {
            "a(%s) %s b(%s): ".printf(x, op, y)
            eval "a(Bool(x)) #{op} b(Bool(y))"
            print "\n"
        }
    }
}
 
# Test and display
test()
```

#### Output:
```
a(1) && b(1): AB
a(1) && b(0): AB
a(0) && b(1): A
a(0) && b(0): A
a(1) || b(1): A
a(1) || b(0): A
a(0) || b(1): AB
a(0) || b(0): AB
```
