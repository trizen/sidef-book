[1]: https://rosettacode.org/wiki/Write_entire_file

# [Write entire file][1]

With error handling:

```ruby
var file = File(__FILE__)
file.open_w(\var fh, \var err) || die "Can't open #{file}: #{err}"
fh.print("Hello world!")       || die "Can't write to #{file}: #{$!}"
```


Without error handling:

```ruby
File(__FILE__).open_w.print("Hello world!")
```