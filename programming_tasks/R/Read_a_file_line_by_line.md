[1]: https://rosettacode.org/wiki/Read_a_file_line_by_line

# [Read a file line by line][1]

*FileHandle.each{}* is lazy, allowing us to do this:

```ruby
File(__FILE__).open_r.each { |line|
    say line
}
```


Same thing explicitly:

```ruby
var fh = File(__FILE__).open_r
while (fh.readline(\var line)) {
    say line
}
```
