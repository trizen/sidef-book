# DirHandle

Abstraction on a directory descriptor, to access the content of a directory:

```ruby
var dh = Dir("/my/path").open
```

Some useful methods on FileHandle objects:

```ruby
dh.read                 # read one entry as a File or a Dir object
dh.entries              # read all entries as an Array of File and Dir objects
dh.files                # read all file entries as an Array of File objects
dh.dirs                 # read all directory entries as an Array of Dir objects
dh.seek(pos)            # set the current position in the directory handle
dh.rewind               # set the current position to the beginning of the directory
dh.tell                 # returns the current position in the directory handle
dh.chdir                # change the working directory to the path of `dh`
dh.each { ... }         # iterate over each entry
dh.close                # close the directory handle
```

The special `DirHandle` type can be for checking if a given object is really a DirHandle object:

```ruby
dh.kind_of(DirHandle)    # true if `dh` is a DirHandle object
```

The directory object to which a DirHandle refers, if any, can be obtained with `dh.dir`, which may be `nil` or a `Dir` object.
