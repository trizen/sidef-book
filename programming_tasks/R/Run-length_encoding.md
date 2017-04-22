[1]: http://rosettacode.org/wiki/Run-length_encoding

# [Run-length encoding][1]

First solution:

```ruby
func encode(str) {
  str.gsub(/((.)(\2*))/, {|a,b| "#{a.len}#{b}" })
}
 
func decode(str) {
  str.gsub(/(\d+)(.)/, {|a,b| b * a.to_i })
}
```

#### Output:
```
12W1B12W3B24W1B14W
```


Second solution, encoding the length into a byte:

```ruby
func encode(str) {
    str.gsub(/(.)(\1{0,254})/, {|a,b| b.len+1 -> chr + a })
}
 
func decode(str) {
     var chars = str.chars
     var r = ''
     {|i|
         r += (chars[2*i + 1] * chars[2*i].ord)
     } << ^(chars.len//2)
     return r
}
```

#### Output:
```
"\fW\1B\fW\3B\30W\1B\16W"
```
