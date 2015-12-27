[1]: http://rosettacode.org/wiki/Extract_file_extension

# [Extract file extension][1]

```ruby
func extension (filename) {
   given(filename.split('.').last) {
       when(filename) { "" }
       when(/[\/_]/)  { "" }
       default        { "." + _ }
   }
}
 
['mywebsite.com/picture/image.png',
 'http://mywebsite.com/picture/image.png',
 'myuniquefile.longextension',
 'IAmAFileWithoutExtension',
 '/path/to.my/file',
 'file.odd_one',
].each {|f| say "#{f} -> #{extension(f).dump}" }
```

#### Output:
```
mywebsite.com/picture/image.png -> ".png"
http://mywebsite.com/picture/image.png -> ".png"
myuniquefile.longextension -> ".longextension"
IAmAFileWithoutExtension -> ""
/path/to.my/file -> ""
file.odd_one -> ""
```