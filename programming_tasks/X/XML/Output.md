[1]: https://rosettacode.org/wiki/XML/Output

# [XML/Output][1]

```ruby
require('XML::Mini::Document')
 
var students = [
                ["April",         "Bubbly: I'm > Tam and <= Emily"],
                ["Tam O'Shanter", "Burns: \"When chapman billies leave the street ...\""],
                ["Emily",         "Short & shrift"]
               ]
 
var doc   = %O<XML::Mini::Document>.new
var root  = doc.getRoot
var studs = root.createChild("CharacterRemarks")
 
students.each { |s|
    var stud = studs.createChild("Character")
    stud.attribute("name", s[0])
    stud.text(s[1])
}
 
print doc.toString
```
