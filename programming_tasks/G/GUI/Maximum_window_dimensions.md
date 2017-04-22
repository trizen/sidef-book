[1]: http://rosettacode.org/wiki/GUI/Maximum_window_dimensions

# [GUI/Maximum window dimensions][1]

Using the Tk library:

```ruby
require('Tk')
 
func max_window_size() -> (Number, Number) {
    %O<MainWindow>.new.maxsize
}
 
var (width, height) = max_window_size()
say (width, 'x', height)
```

#### Output:
```
1905x1050
```
