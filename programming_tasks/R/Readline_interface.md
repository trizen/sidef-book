[1]: https://rosettacode.org/wiki/Readline_interface

# [Readline interface][1]

```ruby
require('Term::ReadLine')
 
var term = %O<Term::ReadLine>.new('Example')
 
term.addhistory('foo')
term.addhistory('bar')
 
loop {
    var cmd = term.readline("Prompt: ") \\ break
 
    if (cmd ~~ %w[q quit]) {
        break
    }
 
    say "You inserted <<#{cmd}>>"
}
```