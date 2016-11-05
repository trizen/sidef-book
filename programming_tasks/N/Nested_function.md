[1]: http://rosettacode.org/wiki/Nested_function

# [Nested function][1]

```ruby
func make_list(separator = ') ') {
 
    var count = 1
    func make_item(item) {
        [count++, separator, item].join
    }
 
    <first second third> «call« make_item -> join("\n")
}
 
say make_list('. ')
```

#### Output:
```
1. first
2. second
3. third
```