[1]: http://rosettacode.org/wiki/File_modification_time

# [File modification time][1]

```ruby
var file = File(__FILE__)
say file.stat.mtime            # seconds since the epoch
 
# keep atime unchanged
# set mtime to current time
file.utime(file.stat.atime, Time.now)
```
