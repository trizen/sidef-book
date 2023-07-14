[1]: https://rosettacode.org/wiki/XML/XPath

# [XML/XPath][1]

```ruby
require('XML::XPath')

var x = %O<XML::XPath>.new(ARGF.slurp)

[x.findnodes('//item[1]')][0]
say [x.findnodes('//price')].map{x.getNodeText(_)}
[x.findnodes('//name')]
```

#### Output:
```
[14.5, 23.99, 4.95, 3.56]
```
