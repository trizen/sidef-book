[1]: https://rosettacode.org/wiki/Simple_windowed_application

# [Simple windowed application][1]

### Gtk2

```ruby
require('Gtk2') -> init

# Window.
var window = %O<Gtk2::Window>.new
window.signal_connect('destroy' => { %O<Gtk2>.main_quit })

# VBox.
var vbox = %O<Gtk2::VBox>.new(0, 0)
window.add(vbox)

# Label.
var label = %O<Gtk2::Label>.new('There have been no clicks yet.')
vbox.add(label)

# Button.
var count = 0
var button = %O<Gtk2::Button>.new(' Click Me ')
vbox.add(button)
button.signal_connect('clicked' => {
    label.set_text(++count)
})

# Show.
window.show_all

# Main loop.
%O<Gtk2>.main
```

### Gtk3

```ruby
use('Gtk3 -init')

# Window.
var window = %O'Gtk3::Window'.new
window.signal_connect('destroy' => { %O'Gtk3'.main_quit })

# VBox.
var vbox = %O'Gtk3::VBox'.new(0, 0)
window.add(vbox)

# Label.
var label = %O'Gtk3::Label'.new('There have been no clicks yet.')
vbox.add(label)

# Button.
var count = 0
var button = %O'Gtk3::Button'.new(' Click Me ');
vbox.add(button)
button.signal_connect('clicked' => {
    label.set_text(++count)
})

# Show.
window.show_all

# Main loop.
%O'Gtk3'.main
```
