[1]: https://rosettacode.org/wiki/Keyboard_input/Obtain_a_Y_or_N_response

# [Keyboard input/Obtain a Y or N response][1]

```ruby
func prompt_yn {
    static rk = frequire('Term::ReadKey')
    rk.ReadMode(4)     # change to raw input mode
 
    var key = ''
    while (key !~ /[yn]/i) {
        while (rk.ReadKey(-1) != nil) {}   # discard any previous input
        print "Type Y/N: "
        say (key = rk.ReadKey(0))          # read a single character
    }
 
    rk.ReadMode(0)     # reset the terminal to normal mode
    return key.uc
}
 
var key = prompt_yn()
say "You typed: #{key}"
```

#### Output:
```
Type Y/N: a
Type Y/N: b
Type Y/N: c
Type Y/N: y
You typed: Y
```
