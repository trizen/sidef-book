# FileHandle

A FileHandle, or File object represents a local file. The literal syntax `%f` can be used:

```ruby
FileHandle("/path/to/file.ext")
File("/path/to/file.ext")
%f(/path/to/file.ext)
```

Many operations are defined on FileHandles, from reading / writing to checksums to path operations.
