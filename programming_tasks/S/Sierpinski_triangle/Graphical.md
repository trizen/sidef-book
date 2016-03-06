[1]: http://rosettacode.org/wiki/Sierpinski_triangle/Graphical

# [Sierpinski triangle/Graphical][1]

Creates a PNG image.

```ruby
func sierpinski_triangle(n) -> Array {
  var triangle = ['*'];
  { |i|
    var sp = (' ' * Math.pow(2, i-1));
    triangle = (triangle.map {|x| sp + x + sp} +
                triangle.map {|x| x + ' ' + x});
  } * n;
  triangle;
}
 
class Array {
  method to_png(scale=1, bgcolor='white', fgcolor='black') {
 
    var gd = (
      try   { require('GD::Simple') }
      catch { warn("GD::Simple is not installed!"); return };
    );
 
    var width = self.max_by{.len}.len;
    self.map!{|r| "%-#{width}s" % r};
 
    var img = gd.new(width * scale, self.len * scale);
 
    self.range.each { |i|
      range(i * scale, i * scale + scale).each { |j|
        var row = self[i];
        img.moveTo(0, j);
        loop {
          if ((var sp = row.count(/^\s+/)) > 0) {
             row.substr!(sp);
             img.fgcolor(bgcolor);
             img.line(scale * sp);
          }
          elsif ((var nsp = row.count(/^\S+/)) > 0) {
             row.substr!(nsp);
             img.fgcolor(fgcolor);
             img.line(scale * nsp);
          }
          else {
             break;
          }
        }
      }
    }
 
    return img.png;
  }
}
 
var triangle = sierpinski_triangle(8);
var raw_png = triangle.to_png(bgcolor:'black', fgcolor:'red');
 
var file = %f'triangle.png';
file.open('>:raw', \var fh, \var err)
    || die "Can't write to file '#{file}': #{err}";
fh.print(raw_png);
fh.close;
```
