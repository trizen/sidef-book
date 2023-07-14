[1]: https://rosettacode.org/wiki/Secure_temporary_file

# [Secure temporary file][1]

```ruby
var tmpfile = require('File::Temp')
var fh = tmpfile.new(UNLINK => 0)
say fh.filename
fh.print("Hello, World!\n")
fh.close
```
