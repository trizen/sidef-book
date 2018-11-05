# File

A File object represents a local file. The literal syntax `%f` can be used:

```ruby
File("/path/to/file.ext")
%f(/path/to/file.ext)
```

A file can be opened for reading or writing, using the `open_r` and `open_w` methods, respectively:

```ruby
var file = File("file.txt")    # File object
var fh = file.open_r           # FileHandle object
say fh.lines                   # read the lines into an Array
```

Many operations are defined on FileHandles, from reading / writing to checksums to path operations.
