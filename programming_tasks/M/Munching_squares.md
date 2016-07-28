[1]: http://rosettacode.org/wiki/Munching_squares

# [Munching squares][1]

```ruby
require('GD')

var img = %s<GD::Image>.new(256, 256, 1)

for y,x in (^256 ~X ^256) {
    var color = img.colorAllocate((255 - x - y).abs, (255-x)^y, x^(255-y))
    img.setPixel(x, y, color)
}

File('xor.png').write(img.png, :raw)
```
