[1]: https://rosettacode.org/wiki/Walk_a_directory/Recursively

# [Walk a directory/Recursively][1]

```ruby
func traverse(Block callback, Dir dir) {
    dir.open(\var dir_h) || return nil
 
    dir_h.entries.each { |entry|
        if (entry.is_a(Dir)) {
            traverse(callback, entry)
        } else {
            callback(entry)
        }
    }
}
 
var dir = Dir.cwd
var pattern = /foo/   # display files that contain 'foo'
 
traverse(
    { |file|
        if (file.basename ~~ pattern) {
            say file
        }
    } => dir
)
```
