[1]: http://rosettacode.org/wiki/Roots_of_a_function

# [Roots of a function][1]

```ruby
func f(x) {
    x*x*x - 3*x*x + 2*x;
}
 
var step = 0.001;
var start = -1;
var stop = 3;
 
start+step ..^ (stop, step).each { |x|
    static sign = false;
    given (var value = f(x))
        when (0) {
            say "Root found at #{x}";
        }
        case (sign && ((value > 0) != sign)) {
            say "Root found near #{x}";
        };
    sign = value>0;
}
```

#### Output:
```
Root found at 0
Root found at 1
Root found at 2
```