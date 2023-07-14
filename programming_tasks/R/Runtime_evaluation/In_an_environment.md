[1]: https://rosettacode.org/wiki/Runtime_evaluation/In_an_environment

# [Runtime evaluation/In an environment][1]

```ruby
func eval_with_x(code, x, y) {
    var f = eval(code)
    x = y
    eval(code) - f
}
 
say eval_with_x(x: 3, y: 5, code: '2 ** x')   # => 24
```
