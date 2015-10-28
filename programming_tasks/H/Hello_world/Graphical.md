[1]: http://rosettacode.org/wiki/Hello_world/Graphical

# [Hello world/Graphical][1]

```ruby
var tk = require 'Tk';
var main = %s'MainWindow'.new;
main.Button(
    '-text'    => 'Goodbye, World!',
    '-command' => 'exit',
).pack;
tk.MainLoop;
```
```ruby
var gtk2 = require('Gtk2') -> init;
 
var window = %s'Gtk2::Window'.new;
var label  = %s'Gtk2::Label'.new('Goodbye, World!');
 
window.set_title('Goodbye, World!');
window.signal_connect(destroy => { gtk2.main_quit });
 
window.add(label);
window.show_all;
 
gtk2.main;
```