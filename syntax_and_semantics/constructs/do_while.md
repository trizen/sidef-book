# do/while

A `do/while` construct guarantees the execution of the block at least once.

```ruby
var name = ''

do {
    name = read("username: ", String)
} while(name ~~ /^(root|)\z/)

say "Your username is #{name}"
```
