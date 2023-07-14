[1]: https://rosettacode.org/wiki/Regular_expressions

# [Regular expressions][1]

Simple matching:

```ruby
var str = "I am a string"
if (str =~ /string$/) {
    print "Ends with 'string'\n"
}
```


Global matching:

```ruby
var str = <<'EOF'
    x:Foo
    y:Bar
EOF
 
while (var m = str=~/(\w+):(\S+)/g) {
    say "#{m[0]} -> #{m[1]}"
}
```


Substitutions:

```ruby
var str = "I am a string"
 
# Substitute something mached by a regex
str.sub!(/ a /, ' another ')   # "I am a string" => "I am another string"
 
# Remove something matched by a regex
str -= / \Kanother /i          # "I am another string" => "I am string"
 
# Global subtitution with a block
str = str.gsub(/(\w+)/, {|s1| 'x' * s1.len})  # globaly replace any word with 'xxx'
 
say str     # prints: 'x xx xxxxxx'
```
