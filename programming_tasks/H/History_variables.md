[1]: https://rosettacode.org/wiki/History_variables

# [History variables][1]

Implemented as a class:

```ruby
class HistoryVar(v) {
 
    has history = []
    has variable = v
 
    method ≔(value) {
        history << variable
        variable = value
    }
 
    method to_s {
        "#{variable}"
    }
 
    method AUTOLOAD(_, name, *args) {
        variable.(name)(args...)
    }
}
 
var foo = HistoryVar(0)
 
foo ≔ 1
foo ≔ 2
foo ≔ foo+3
foo ≔ 42
 
say "History: #{foo.history}"
say "Current value: #{foo}"
```

#### Output:
```
History: [0, 1, 2, 5]
Current value: 42
```