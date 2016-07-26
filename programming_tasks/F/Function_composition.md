[1]: http://rosettacode.org/wiki/Function_composition

# [Function composition][1]

```ruby
func compose(f, g) {
    func(x) { f(g(x)) }
}
var fg = compose(func(x){Math.sin(x)}, func(x){Math.cos(x)})
say fg(0.5)      # => 0.76919635484100842185251475805107
```
