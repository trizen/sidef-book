[1]: https://rosettacode.org/wiki/Fractal_tree

# [Fractal tree][1]

```ruby
func tree(img, x, y, scale=6/10, len=400, angle=270) {

    len < 1 && return()

    img.moveTo(x, y)
    img.angle(angle)
    img.line(len)

    var (x1, y1) = img.curPos
    tree(img, x1, y1, scale, len*scale, angle+35)
    tree(img, x1, y1, scale, len*scale, angle-35)
}

require('GD::Simple')

var (width=1000, height=1000)
var img = %s<GD::Simple>.new(width, height)
img.fgcolor('black')
img.penSize(1, 1)

tree(img, width/2, height)

File('tree.png').write(img.png, :raw)
```
