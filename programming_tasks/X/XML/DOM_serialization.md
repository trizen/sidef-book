[1]: http://rosettacode.org/wiki/XML/DOM_serialization

# [XML/DOM serialization][1]

```ruby
require('XML::Simple')
print %S'XML::Simple'.XMLout(
    :(root => :( element => 'Some text here' )),
    NoAttr => 1, RootName => '',
)
```

#### Output:
```
  <root>
    <element>Some text here</element>
  </root>
```
