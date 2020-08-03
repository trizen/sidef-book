# File

A File object represents the name of a local file:

```ruby
File("/path/to/file.ext")
```

Alternatively:

```ruby
%f(/path/to/file.ext)
%d(/path/to) + %f(file.ext)
```

A file can be opened for reading or writing, using the `open_r` and `open_w` methods, respectively:

```ruby
var file = File("file.txt")    # File object
var fh = file.open_r           # FileHandle object
say fh.lines                   # read the lines into an Array
```

Creating a new file:

```ruby
var fh = File("newfile.txt").open_w
fh.say("foo")   # write a newline to the file
fh.close        # close the filehandle
```

A File abstracts an entity on the filesystem by name; a FileHandle abstracts a file descriptor in memory.

```ruby
File("file.txt").read           # read the content of a file as a String (UTF-8)
File("file.txt").read(:raw)     # read the content of a file as a String (RAW)
```

See the [FileHandle](filehandle.md) documentation for more information.
