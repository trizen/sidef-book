[1]: http://rosettacode.org/wiki/Terminal_control/Preserve_screen

# [Terminal control/Preserve screen][1]

```ruby
print "\e[?1049h\e[H";
say "Alternate buffer!";
 
3.downto(1).each { |i|
    say "Going back in: #{i}";
    Sys.sleep(1);
}
 
print "\e[?1049l";
```