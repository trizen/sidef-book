[1]: https://rosettacode.org/wiki/Hough_transform

# [Hough transform][1]

```ruby
require('Imager')
 
func hough(im, width=460, height=360) {
 
    height = 2*floor(height / 2)
 
    var xsize = im.getwidth
    var ysize = im.getheight
 
    var ht = %O<Imager>.new(xsize => width, ysize => height)
    var canvas = height.of { width.of(255) }
 
    ht.box(filled => true, color => 'white')
 
    var rmax = hypot(xsize, ysize)
    var dr = 2*(rmax / height)
    var dth = (Num.pi / width)
 
    for y,x in (^ysize ~X ^xsize) {
        var col = im.getpixel(x => x, y => y)
        var (r,g,b) = col.rgba
        (r==255 && g==255 && b==255) && next
        for k in ^width {
            var th = dth*k
            var r = (x*cos(th) + y*sin(th))
            var iry = (height/2 + int(r/dr + 0.5))
            ht.setpixel(x => k, y => iry, color => 3.of(--canvas[iry][k]))
        }
    }
 
    return ht
}
 
var img = %O<Imager>.new(file => 'Pentagon.png')
var ht = hough(img)
ht.write(file => 'Hough transform.png')
```
