[1]: http://rosettacode.org/wiki/Simple_windowed_application

# [Simple windowed application][1]

```ruby
require('Gtk2') -> init;

# Window.
var window = %s'Gtk2::Window'.new;
window.signal_connect('destroy' => func(*_) { %s'Gtk2'.main_quit });

# VBox.
var vbox = %s'Gtk2::VBox'.new(0, 0);
window.add(vbox);

# Label.
var label = %s'Gtk2::Label'.new('There have been no clicks yet.');
vbox.add(label);

# Button.
var count = 0;
var button = %s'Gtk2::Button'.new(' Click Me ');
vbox.add(button);
button.signal_connect('clicked' => func(*_) {
    label.set_text(++count);
});

# Show.
window.show_all;

# Main loop.
%s'Gtk2'.main;
```
