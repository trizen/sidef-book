[1]: http://rosettacode.org/wiki/Sierpinski_triangle/Graphical

# [Sierpinski triangle/Graphical][1]

Creates a PNG image.

```ruby
func sierpinski_triangle(n) -> Array {
  var triangle = ['*']
  { |i|
    var sp = (' ' * Math.pow(2, i-1));
    triangle = (triangle.map {|x| sp + x + sp} +
                triangle.map {|x| x + ' ' + x})
  } * n
  triangle
}

class Array {
  method to_png(scale=1, bgcolor='white', fgcolor='black') {

    var gd = (
      try   { require('GD::Simple') }
      catch { warn "GD::Simple is not installed!"; return }
    );

    var width = self.max_by{.len}.len
    self.map!{|r| "%-#{width}s" % r}

    var img = gd.new(width * scale, self.len * scale)

    for i in ^self {
      for j in RangeNum(i*scale, i*scale + scale) {
        var row = self[i]
        img.moveTo(0, j)
        var len = row.len
        while (len) {
          row.gsub!(/^\s+/)
          var color = bgcolor
          if (len == row.len) {
            row.gsub!(/^\S+/)
            color = fgcolor
          }
          img.fgcolor(color)
          var p = len-row.len
          len = row.len
          img.line(scale * p)
        }
      }
    }
    img.png
  }
}

var triangle = sierpinski_triangle(8)
var raw_png = triangle.to_png(bgcolor:'black', fgcolor:'red')

var file = %f'triangle.png'
var fh = file.open('>:raw')
fh.print(raw_png)
fh.close
```
