[1]: http://rosettacode.org/wiki/Julia_set

# [Julia set][1]

```ruby
require('Imager')
 
var (w, h) = (640, 480)
var img = %s'Imager'.new(xsize => w, ysize => h, channels => 3)
 
var maxIter = 50
var (cX, cY) = (-0.388, 0.613)
 
var color = %s'Imager::Color'.new('#000000')
 
for x,y in (^w ~X ^h) {
    var (tmp1, tmp2, i, zx, zy) = (
        0, 0, maxIter,
        float((x - w/2) / w * 3),
        float((y - h/2) / h * 2),
    )
    loop {
        (tmp1, tmp2) = (zx*zx, zy*zy)
        ((tmp1+tmp2 < 4) && (--i -> is_pos)) || break
        (zy, zx) = (float(2 * zx*zy + cY), float(tmp1 - tmp2 + cX))
    }
    color.set(hsv => [i / maxIter * 360, 1, i])
    img.setpixel(x => x, y => y, color => color)
}
 
img.write(file => "JuliaSet_sidef.png")
```