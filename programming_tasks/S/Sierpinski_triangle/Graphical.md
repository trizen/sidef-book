[1]: https://rosettacode.org/wiki/Sierpinski_triangle/Graphical

# [Sierpinski triangle/Graphical][1]

Creates a PNG image.

```ruby
func sierpinski_triangle(n) -> Array {
  var triangle = ['*']
  { |i|
    var sp = (' ' * 2**i)
    triangle = (triangle.map {|x| sp + x + sp} +
                triangle.map {|x| x + ' ' + x})
  } * n
  triangle
}

class Array {
  method to_png(scale=1, bgcolor='white', fgcolor='black') {

    static gd = require('GD::Simple')
    var width = self.max_by{.len}.len
    self.map!{|r| "%-#{width}s" % r}

    var img = gd.new(width * scale, self.len * scale)

    for i in ^self {
      for j in RangeNum(i*scale, i*scale + scale) {
        img.moveTo(0, j)
        for line in (self[i].scan(/(\s+|\S+)/)) {
          img.fgcolor(line.contains(/\S/) ? fgcolor : bgcolor)
          img.line(scale * line.len)
        }
      }
    }
    img.png
  }
}

var triangle = sierpinski_triangle(8)
var raw_png = triangle.to_png(bgcolor:'black', fgcolor:'red')
File('triangle.png').write(raw_png, :raw)
```
