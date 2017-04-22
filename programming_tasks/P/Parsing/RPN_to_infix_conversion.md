[1]: http://rosettacode.org/wiki/Parsing/RPN_to_infix_conversion

# [Parsing/RPN to infix conversion][1]

```ruby
func p(pair, prec) {
    pair[0] < prec ? "( #{pair[1]} )" : pair[1]
}
 
func rpm_to_infix(string) {
    say "#{'='*17}\n#{string}"
    var stack = []
    string.each_word { |w|
        if (w ~~ /\d/) {
            stack << [9, Num(w)]
        }
        else {
            var y = stack.pop
            var x = stack.pop
            given(w) {
              when ('^')   { stack << [4, [p(x,5), w, p(y,4)].join(' ')] }
              when (<* />) { stack << [3, [p(x,3), w, p(y,3)].join(' ')] }
              when (<+ ->) { stack << [2, [p(x,2), w, p(y,2)].join(' ')] }
            }
            say stack
        }
    }
    say '-'*17
    stack.map{_[1]}
}
 
var tests = [
    '3 4 2 * 1 5 - 2 3 ^ ^ / +',
    '1 2 + 3 4 + ^ 5 6 + ^',
]
 
tests.each { say rpm_to_infix(_).join(' ') }
```

#### Output:
```
=================
3 4 2 * 1 5 - 2 3 ^ ^ / +
[[9, 3], [3, "4 * 2"]]
[[9, 3], [3, "4 * 2"], [2, "1 - 5"]]
[[9, 3], [3, "4 * 2"], [2, "1 - 5"], [4, "2 ^ 3"]]
[[9, 3], [3, "4 * 2"], [4, "( 1 - 5 ) ^ 2 ^ 3"]]
[[9, 3], [3, "4 * 2 / ( 1 - 5 ) ^ 2 ^ 3"]]
[[2, "3 + 4 * 2 / ( 1 - 5 ) ^ 2 ^ 3"]]
-----------------
3 + 4 * 2 / ( 1 - 5 ) ^ 2 ^ 3
=================
1 2 + 3 4 + ^ 5 6 + ^
[[2, "1 + 2"]]
[[2, "1 + 2"], [2, "3 + 4"]]
[[4, "( 1 + 2 ) ^ ( 3 + 4 )"]]
[[4, "( 1 + 2 ) ^ ( 3 + 4 )"], [2, "5 + 6"]]
[[4, "( ( 1 + 2 ) ^ ( 3 + 4 ) ) ^ ( 5 + 6 )"]]
-----------------
( ( 1 + 2 ) ^ ( 3 + 4 ) ) ^ ( 5 + 6 )
```
