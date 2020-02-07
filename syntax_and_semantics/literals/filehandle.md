# FileHandle

Abstraction on a file descriptor, to interact with the content of a file.

```ruby
var a = File("existing_file.txt").open_r      # open file for reading
var b = File("new_file.txt").open_w           # open file for writing
```

Some useful methods on FileHandle objects:

```ruby
fh.autoflush(bool)      # enable/disable auto-flush mode
fh.binmode(encoding)    # set encoding
fh.line                 # read one line as a String
fh.slurp                # read the entire file as a String
fh.lines                # read the entire file as an Array of String objects
fh.grep { ... }         # collect only the lines that match the block
fh.grep(/regex/)        # collect only the lines that match the regex
fh.each { ... }         # iterate over each line
fh.eof                  # true when at the end of the file
fh.tell                 # current position in the file
fh.seek(pos,whence)     # jump to this position in the file
fh.lock                 # lock the filehandle
fh.unlock               # unlock the filehandle
fh.say(str)             # write a string into the file (appending "\n")
fh.print(str)           # write a string into the file (without appending "\n")
fh.close                # close the filehandle
```

The special `FileHandle` type can be for checking if a given object is really a FileHandle object:

```ruby
fh.kind_of(FileHandle)    # true if `fh` is a FileHandle object
```

The file object to which a FileHandle refers, if any, can be obtained with `fh.file`, which may be `nil` or a `File` object.
