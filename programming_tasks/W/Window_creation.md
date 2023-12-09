[1]: https://rosettacode.org/wiki/Window_creation

# [Window creation][1]

### Tk

```ruby
require('Tk')
%s'MainWindow'.new
%S'Tk'.MainLoop
```


### Gtk2

```ruby
var gtk2 = require('Gtk2') -> init
var window = %s'Gtk2::Window'.new
window.signal_connect(destroy => { gtk2.main_quit })
window.show_all
gtk2.main
```
