[1]: http://rosettacode.org/wiki/Partial_function_application

# [Partial function application][1]

```ruby
func fs(f) {
    func(*args) {
        args.map {f(_)}
    }
}
 
func double(n) { n  * 2 }
func square(n) { n ** 2 }
 
var fs_double = fs(double)
var fs_square = fs(square)
 
var s = @(0 .. 3)
say "fs_double(#{s}): #{fs_double(s...)}"
say "fs_square(#{s}): #{fs_square(s...)}"
 
s = [2, 4, 6, 8]
say "fs_double(#{s}): #{fs_double(s...)}"
say "fs_square(#{s}): #{fs_square(s...)}"
```

#### Output:
```
fs_double(0 1 2 3): 0 2 4 6
fs_square(0 1 2 3): 0 1 4 9
fs_double(2 4 6 8): 4 8 12 16
fs_square(2 4 6 8): 4 16 36 64
```
