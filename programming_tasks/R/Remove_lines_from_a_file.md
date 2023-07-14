[1]: https://rosettacode.org/wiki/Remove_lines_from_a_file

# [Remove lines from a file][1]

```ruby
func remove_lines(file, beg, len) {
    var lines = file.open_r.lines
    lines.splice(beg, len).len == len || warn "Too few lines";
    file.write(lines.join("\n"), :utf8)
}

remove_lines(File(__FILE__), 2, 3)
```
