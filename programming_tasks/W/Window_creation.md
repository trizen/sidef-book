[1]: http://rosettacode.org/wiki/Window_creation

# [Window creation][1]

```ruby
var tk = require 'Tk';
'MainWindow'.to_caller.new;
tk.MainLoop;
```
```ruby
Perl.eval('use Gtk2 qw(-init)');
var gtk2   = 'Gtk2'.to_caller;
var window = 'Gtk2::Window'.to_caller.new;
window.signal_connect(destroy => { gtk2.main_quit });
window.show_all;
gtk2.main;
```