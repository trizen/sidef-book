[1]: http://rosettacode.org/wiki/Read_a_specific_line_from_a_file

# [Read a specific line from a file][1]

```ruby
func getNthLine(filename, n) {
  var file = File(filename);
  file.open_r.each { |line|
    Num($.) == n && return line;
  }
  warn "file #{file} does not have #{n} lines, only #{$.}\n";
  return nil;
}
 
var line = getNthLine("/etc/passwd", 7);
print line if defined line;
```
