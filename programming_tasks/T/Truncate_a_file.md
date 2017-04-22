[1]: http://rosettacode.org/wiki/Truncate_a_file

# [Truncate a file][1]

```ruby
func truncate(filename, len) {
    var file = File(filename)
    len > file.size ->
        && die "The provided length is greater than the length of the file"
    file.truncate(len)
}

# truncate "file.ext" to 1234 bytes
truncate("file.ext", 1234)
```
