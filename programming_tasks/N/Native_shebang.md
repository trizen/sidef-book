[1]: https://rosettacode.org/wiki/Native_shebang

# [Native shebang][1]

Sidef is a scripting language and does not compile to a binary.

```ruby
#!/usr/bin/sidef
say ARGV.join(" ")
```

#### Output:
```
$ ./echo.sf Hello, World!
Hello, World!
```