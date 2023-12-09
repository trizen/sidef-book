[1]: https://rosettacode.org/wiki/String_length

# [String length][1]

```ruby
var str = "J\x{332}o\x{332}s\x{332}e\x{301}\x{332}"
```


### Byte Length



UTF-8 byte length (default):

```ruby
say str.bytes.len       #=> 14
```


UTF-16 byte length:

```ruby
say str.encode('UTF-16').bytes.len      #=> 20
```


### Character Length

```ruby
say str.chars.len    #=> 9
```


### Grapheme Length

```ruby
say str.graphs.len   #=> 4
```
