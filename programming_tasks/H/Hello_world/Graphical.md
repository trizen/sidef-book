[1]: http://rosettacode.org/wiki/Hello_world/Graphical

# [Hello world/Graphical][1]

```ruby
var tk = require 'Tk';
var main = 'MainWindow'.to_caller.new;
main.Button(
    '-text'    => 'Goodbye, World!',
    '-command' => 'exit',
).pack;
tk.MainLoop;
```
```ruby
Perl.eval('use Gtk2 qw(-init)');
 
var gtk2   = 'Gtk2'.to_caller;
var window = 'Gtk2::Window'.to_caller.new;
var label  = 'Gtk2::Label'.to_caller.new('Goodbye, World!');
 
window.set_title('Goodbye, World!');
window.signal_connect(destroy => { gtk2.main_quit });
 
window.add(label);
window.show_all;
 
gtk2.main;
```