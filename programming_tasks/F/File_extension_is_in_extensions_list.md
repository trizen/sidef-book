[1]: http://rosettacode.org/wiki/File_extension_is_in_extensions_list

# [File extension is in extensions list][1]

```ruby
func check_extension(filename, extensions) {
    filename ~~ Regex('\.(' + extensions.map { .escape }.join('|') + ')\z', :i)
}
```


Testing:

```ruby
var extensions = ['zip', 'rar', '7z', 'gz', 'archive', 'A##', 'tar.bz2']
 
var files = [
    'MyData.a##', 'MyData.tar.Gz', 'MyData.gzip', 'MyData.7z.backup',
    'MyData...', 'MyData', 'MyData_v1.0.tar.bz2', 'MyData_v1.0.bz2'
]
 
for file in files {
    printf("%-19s - %s\n", file, check_extension(file, extensions))
}
```

#### Output:
```
MyData.a##          - true
MyData.tar.Gz       - true
MyData.gzip         - false
MyData.7z.backup    - false
MyData...           - false
MyData              - false
MyData_v1.0.tar.bz2 - true
MyData_v1.0.bz2     - false
```