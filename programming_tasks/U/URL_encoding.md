[1]: http://rosettacode.org/wiki/URL_encoding

# [URL encoding][1]

```ruby
func urlencode(str) {
    str.gsub!(%r"([^-A-Za-z0-9_.!~*'() ])", {|a| "%%%02X" % a.ord })
    str.gsub!(' ', '+')
    return str
}
 
say urlencode('http://foo bar/')
```

#### Output:
```
http%3A%2F%2Ffoo+bar%2F
```
