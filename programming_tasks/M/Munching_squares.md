[1]: http://rosettacode.org/wiki/Munching_squares

# [Munching squares][1]

```ruby
require('GD')
 
var gd_img = %s<GD::Image>
var img = gd_img.new(256, 256, 1)
 
for y in ^256 {
    for x in ^256 {
        var color = img.colorAllocate((255 - x - y).abs, (255-x)^y, x^(255-y))
        img.setPixel(x, y, color)
    }
}
 
if (var fh = %f(xor.png).open('>:raw')) {
    fh << img.png
}
```
