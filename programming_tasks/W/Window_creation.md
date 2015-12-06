[1]: http://rosettacode.org/wiki/Window_creation

# [Window creation][1]

```ruby
var tk = require('Tk');
%s'MainWindow'.new;
tk.MainLoop;
```
```ruby
var gtk2 = require('Gtk2') -> init;
var window = %s'Gtk2::Window'.new;
window.signal_connect(destroy => func(*_) { gtk2.main_quit });
window.show_all;
gtk2.main;
```
