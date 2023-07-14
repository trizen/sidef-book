[1]: https://rosettacode.org/wiki/Sleep

# [Sleep][1]

```ruby
var sec = read(Number)        # any positive number (it may be fractional)
say "Sleeping for #{sec} sec..."
Sys.sleep(sec)                # in seconds
#Sys.usleep(sec)              # in microseconds
#Sys.nanosleep(sec)           # in nanoseconds
say "Awake!"
```
