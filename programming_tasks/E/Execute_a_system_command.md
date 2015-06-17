[1]: http://rosettacode.org/wiki/Execute_a_system_command

# [Execute a system command][1]

```ruby
# Pipe in read-only mode
%p(ls).open_r.each { |line|
    print line;
};
 
var str1 = `ls`;         # backtick: returns a string
var str2 = %x(ls);       # ditto, alternative syntax
 
Sys.system('ls');   # system: executes a command and prints the result
Sys.exec('ls');     # replaces current process with another
```