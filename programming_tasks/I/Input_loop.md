[1]: https://rosettacode.org/wiki/Input_loop

# [Input loop][1]

To read from the standard input, you can use *STDIN* as your *fh*.

```ruby
var file = File(__FILE__)
file.open_r(\var fh, \var err) || die "#{file}: #{err}"

fh.each { |line|              # iterates the lines of the fh
    line.each_word { |word|   # iterates the words of the line
        say word
    }
}
```
