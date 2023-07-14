[1]: https://rosettacode.org/wiki/Multiline_shebang

# [Multiline shebang][1]

```ruby
#!/bin/sh
 
#`(if running under some shell) {
    eval 'exec /usr/bin/sidef $0 ${1+"$@"} "world"'
}
 
say "Hello, #{ARGV[0]}!"
```

#### Output:
```
$ ./script.sf
Hello, world!

$ ./script.sf Sidef
Hello, Sidef!

$ sidef script.sf RosettaCode
Hello, RosettaCode!
```