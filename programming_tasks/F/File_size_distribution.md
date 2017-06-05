[1]: https://rosettacode.org/wiki/File_size_distribution

# [File size distribution][1]

```ruby
func traverse(Block callback, Dir dir) {
    dir.open(\var dir_h) || return nil
 
    for entry in (dir_h.entries) {
        if (entry.kind_of(Dir)) {
            traverse(callback, entry)
        } else {
            callback(entry)
        }
    }
}
 
var dir = (ARGV ? Dir(ARGV[0]) : Dir.cwd)
 
var group = Hash()
var files_num = 0
var total_size = 0
 
traverse({ |file|
    group{file.size+1 -> log10.round} := 0 += 1
    total_size += file.size
    files_num += 1
}, dir)
 
for k,v in (group.sort_by { |k,_| Num(k) }) {
    say "log10(size) ~~ #{k} -> #{v} files"
}
 
say "Total: #{total_size} bytes in #{files_num} files"
```

#### Output:
```
$ sidef script.sf /usr/bin
log10(size) ~~ 1 -> 4 files
log10(size) ~~ 2 -> 70 files
log10(size) ~~ 3 -> 246 files
log10(size) ~~ 4 -> 1337 files
log10(size) ~~ 5 -> 815 files
log10(size) ~~ 6 -> 167 files
log10(size) ~~ 7 -> 9 files
log10(size) ~~ 8 -> 2 files
Total: 370026462 bytes in 2650 files
```