[1]: https://rosettacode.org/wiki/Menu

# [Menu][1]

```ruby
func menu (prompt, arr) {
    arr.len > 0 || return ''
    loop {
        for i in ^arr {
            say "  #{i}: #{arr[i]}"
        }
        var n = Sys.scanln(prompt) \\ return()
        n ~~ /^[0-9]+\z/ ? Num(n) : next
        arr.exists(n) && return arr[n]
    }
}

var list = ['fee fie', 'huff and puff', 'mirror mirror', 'tick tock']
var prompt = 'Please choose an item number: '

var answer = menu(prompt, list)
say "You choose: #{answer}"
```
