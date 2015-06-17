[1]: http://rosettacode.org/wiki/Read_entire_file

# [Read entire file][1]

Reading an entire file as a string, can be achieved with the *FileHandle.slurp()* method, as illustrated bellow:

```ruby
var file = File.new(__FILE__);
var content = file.open_r.slurp;
print content;
```