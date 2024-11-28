[1]: https://rosettacode.org/wiki/Binary_strings

# [Binary strings][1]

```ruby
# string creation
var x = "hello world"

# string destruction
x = nil

# string assignment with a null byte
x = "a\0b"
say x.length  # ==> 3

# string comparison
if (x == "hello") {
  say "equal"
} else {
  say "not equal"
}

var y = 'bc'
if (x < y) {
  say "#{x} is lexicographically less than #{y}"
}

# string cloning
var xx = x.clone
say (x == xx)                  # true, same length and content
say (x.refaddr == xx.refaddr)  # false, different objects

# check if empty
if (x.is_empty) {
  say "is empty"
}

# append a byte
x += "\07"
say x.dump                  #=> "a\0b\a"

# substring
say x.substr(0, -1).dump    #=> "a\0b"

# replace bytes
say "hello world".tr("l", "L")

# join strings
var a = "hel"
var b = "lo w"
var c = "orld"
var d = (a + b + c)
say d
```

#### Output:
```
3
not equal
ab is lexicographically less than bc
true
true
"a\0b\a"
"a\0b"
heLLo worLd
hello world
```