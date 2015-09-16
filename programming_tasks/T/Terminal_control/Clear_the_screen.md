[1]: http://rosettacode.org/wiki/Terminal_control/Clear_the_screen

# [Terminal control/Clear the screen][1]

Using a cached-function:

```ruby
func clear { print(static x = `clear`) };
clear();
```


Directly invoking the \`clear\` command:

```ruby
Sys.run('clear');
```


Alternatively, without reliance on the command line:

```ruby
print "\e[3J\e[H\e[2J";
```