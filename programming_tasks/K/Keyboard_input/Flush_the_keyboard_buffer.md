[1]: https://rosettacode.org/wiki/Keyboard_input/Flush_the_keyboard_buffer

# [Keyboard input/Flush the keyboard buffer][1]

```ruby
var k = frequire('Term::ReadKey');
 
k.ReadMode('restore');    # Flush the keyboard and returns input stream to initial state
# ReadMode 0;             # Numerical equivalent of keyboard restore (move comment marker to use instead)
 
# A more complete example for use in keyboard handler programming.
# We should also check we are being used in an interactive context (not done here).
 
k.ReadMode('cbreak');
 
# Flush the keyboard in terminal character break mode
while (k.ReadKey(-1) != nil) {
   # Do nothing
}
 
# Don't forget to restore the readmode, when we are finished using the keyboard
k.ReadMode('restore');
```