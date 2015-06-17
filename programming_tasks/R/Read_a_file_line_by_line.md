[1]: http://rosettacode.org/wiki/Read_a_file_line_by_line

# [Read a file line by line][1]

FileHandle.each{} is lazy, so we can do this:

```ruby
File.new(__FILE__).open_r.each { |line|
    print line;
}
```


Same thing explicitly:

```ruby
var fh = File.new(__FILE__).open_r;
while (fh.readline(&var line)) {
    print line;
}
```