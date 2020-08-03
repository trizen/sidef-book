# Sys

The Sys class provides low-level access to various system functions.

```ruby
Sys.run("cmd")        # execute a command
Sys.osname            # name of operating system
Sys.sidef             # path to sidef executable

Sys.kill(:KILL, pid)  # send a "KILL" signal to pid
Sys.fork              # fork the self program
Sys.wait              # wait for a child process to finish

Sys.alarm(n)          # set alarm for n seconds
Sys.sleep(3.5)        # sleep 3.5 seconds
Sys.exit(2)           # exit the program with code 2

Sys.read(TYPE)        # read a type of data from STDIN
Sys.read(msg, TYPE)   # read a type of data from STDIN, with prompt
Sys.scanln(msg)       # read a String line from STDING, with prompt

Sys.refaddr(obj)      # internal reference address of an object
Sys.reftype(obj)      # internal reference type name of an object

Sys.eval(code)        # evaluate arbitrary Perl code
```
