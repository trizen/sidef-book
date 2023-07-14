[1]: https://rosettacode.org/wiki/Determine_if_only_one_instance_is_running

# [Determine if only one instance is running][1]

```ruby
# For this to work, you need to explicitly
# store the returned fh inside a variable.
var fh = File(__FILE__).open_r

# Now call the flock() method on it
fh.flock(File.LOCK_EX | File.LOCK_NB) ->
    || die "I'm already running!"

# Your code here...
say "Running..."
Sys.sleep(20)
say 'Done!'
```
