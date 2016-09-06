[1]: http://rosettacode.org/wiki/Extract_file_extension

# [Extract file extension][1]

```ruby
func extension(filename) {
    filename.match(/(\.[a-z0-9]+)\z/i).to_s
}

var files = [
    'http://example.com/download.tar.gz',
    'CharacterModel.3DS',
    '.desktop',
    'document',
    'document.txt_backup',
    '/etc/pam.d/login',
]

files.each {|f|
    printf("%-36s -> %-11s\n", f.dump, extension(f).dump)
}
```

#### Output:
```
"http://example.com/download.tar.gz" -> ".gz"
"CharacterModel.3DS"                 -> ".3DS"
".desktop"                           -> ".desktop"
"document"                           -> ""
"document.txt_backup"                -> ""
"/etc/pam.d/login"                   -> ""
```
