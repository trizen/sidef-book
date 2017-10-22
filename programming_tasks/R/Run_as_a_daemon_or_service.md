[1]: https://rosettacode.org/wiki/Run_as_a_daemon_or_service

# [Run as a daemon or service][1]

When the "daemon" argument is specified, a fork of the program is created with its STDOUT redirected into the file "foo.txt", and the main process is exited.

```ruby
var block = {
    for n in (1..100) {
        STDOUT.say(n)
        Sys.sleep(0.5)
    }
}
 
if (ARGV[0] == 'daemon') {
    STDERR.say("Daemon mode")
    STDOUT{:fh} = %f'foo.txt'.open_w(){:fh}
    STDOUT.autoflush(true)
    block.fork
    STDERR.say("Exiting")
    Sys.exit(0)
}
 
STDERR.say("Normal mode")
block.run
```