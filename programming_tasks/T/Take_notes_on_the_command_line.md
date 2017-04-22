[1]: http://rosettacode.org/wiki/Take_notes_on_the_command_line

# [Take notes on the command line][1]

```ruby
var file = %f'notes.txt'
 
if (ARGV.len > 0) {
    var fh = file.open_a
    fh.say(Time.local.ctime + "\n\t" + ARGV.join(" "))
    fh.close
} else {
    var fh = file.open_r
    fh && fh.each { .say }
}
```

#### Output:
```
$ sidef notes.sf Test 1
$ sidef notes.sf Test 2
$ sidef notes.sf
Sat Sep 12 00:19:36 2015
        Test 1
Sat Sep 12 00:19:37 2015
        Test 2
```
