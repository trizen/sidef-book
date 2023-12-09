[1]: https://rosettacode.org/wiki/XML_validation

# [XML validation][1]

```ruby
require('XML::LibXML')
 
func is_valid_xml(str, schema) {
 
    var parser    = %O<XML::LibXML>.new
    var xmlschema = %O<XML::LibXML::Schema>.new(string => schema)
 
    try {
        xmlschema.validate(parser.parse_string(str))
        true
    } catch {
        false
    }
}
 
var good_xml = '<a>5</a>'
var bad_xml  = '<a>5<b>foobar</b></a>'
 
var xmlschema_markup = <<'END'
<xsd:schema xmlns:xsd="https://www.w3.org/2001/XMLSchema">
  <xsd:element name="a" type="xsd:integer"/>
</xsd:schema>
END
 
[good_xml, bad_xml].each { |xml|
    say "is_valid_xml(#{xml.dump}) : #{is_valid_xml(xml, xmlschema_markup)}"
}
```

#### Output:
```
is_valid_xml("<a>5</a>") : true
is_valid_xml("<a>5<b>foobar</b></a>") : false
```
