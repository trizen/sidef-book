[1]: http://rosettacode.org/wiki/Parsing/RPN_calculator_algorithm

# [Parsing/RPN calculator algorithm][1]

```ruby
var proggie = '3 4 2 * 1 5 - 2 3 ^ ^ / +';

class RPN(arr=[]) {

    method binop(op) {
        var x = arr.pop
        var y = arr.pop
        arr << y.(op)(x)
    }

    method run(p) {
        p.each_word { |w|
            say "#{w} (#{arr})";
            given (w) {
                when (/\d/) {
                    arr << w.to_f
                }
                when (<+ - * />) {
                    self.binop(w)
                }
                when ('^') {
                    self.binop('**')
                }
                default {
                    die "#{w} is bogus"
                }
            }
        }
        say arr[0]
    }
}

RPN.new.run(proggie);
```

#### Output:
```
3 ()
4 (3)
2 (3 4)
* (3 4 2)
1 (3 8)
5 (3 8 1)
- (3 8 1 5)
2 (3 8 -4)
3 (3 8 -4 2)
^ (3 8 -4 2 3)
^ (3 8 -4 8)
/ (3 8 65536)
+ (3 0.0001220703125)
3.0001220703125
```
