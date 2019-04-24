[1]: https://rosettacode.org/wiki/Modulinos

# [Modulinos][1]

```ruby
# Life.sm
 
func meaning_of_life {
    42
}
 
if (__FILE__ == __MAIN__) {
    say "Main: The meaning of life is #{meaning_of_life()}"
}
```
```ruby
# test.sf
 
include Life
 
say "Test: The meaning of life is #{Life::meaning_of_life()}."
```
