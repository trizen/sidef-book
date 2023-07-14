[1]: https://rosettacode.org/wiki/CSV_to_HTML_translation

# [CSV to HTML translation][1]

```ruby
func escape(str) { str.trans(« & < > », « &amp; &lt; &gt; ») }
func tag(t, d)   { "<#{t}>#{d}</#{t}>" }
 
func csv2html(str) {
 
    var template = <<-'EOT'
    <!DOCTYPE html>
    <html>
    <head><title>Some Text</title></head>
    <body><table>
    %s
    </table></body></html>
    EOT
 
    template.sprintf(escape(str).lines.map{ |line|
            tag('tr', line.split(',').map{|cell| tag('td', cell) }.join)
        }.join("\n")
    )
}
 
var str = <<'EOT';
Character,Speech
The multitude,The messiah! Show us the messiah!
Brians mother,<angry>Now you listen here! He's not the messiah; he's a very naughty boy! Now go away!</angry>
The multitude,Who are you?
Brians mother,I'm his mother; that's who!
The multitude,Behold his mother! Behold his mother!
EOT
 
print csv2html(str)
```
```html5
 
<!DOCTYPE html>
<html>
<head><title>Some Text</title></head>
<body><table>
<tr><td>Character</td><td>Speech</td></tr>
<tr><td>The multitude</td><td>The messiah! Show us the messiah!</td></tr>
<tr><td>Brians mother</td><td>&lt;angry&gt;Now you listen here! He's not the messiah; he's a very naughty boy! Now go away!&lt;/angry&gt;</td></tr>
<tr><td>The multitude</td><td>Who are you?</td></tr>
<tr><td>Brians mother</td><td>I'm his mother; that's who!</td></tr>
<tr><td>The multitude</td><td>Behold his mother! Behold his mother!</td></tr>
</table></body></html>
 
```
