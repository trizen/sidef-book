[1]: https://rosettacode.org/wiki/Bitmap/Bresenham's_line_algorithm

# [Bitmap/Bresenham's line algorithm][1]

```ruby
func my_draw_line(img, x0, y0, x1, y1) {
 
    var steep = (abs(y1 - y0) > abs(x1 - x0))
 
    if (steep) {
        (y0, x0) = (x0, y0)
        (y1, x1) = (x1, y1)
    }
    if (x0 > x1) {
        (x1, x0) = (x0, x1)
        (y1, y0) = (y0, y1)
    }
 
    var deltax = (x1 - x0)
    var deltay = abs(y1 - y0)
    var error  = (deltax / 2)
    var y = y0
    var ystep = (y0 < y1 ? 1 : -1)
 
    for x (x0 .. x1) {
        img.draw_point(steep ? ((y, x)) : ((x, y)))
        error -= deltay
        if (error < 0) {
            y += ystep
            error += deltax
        }
    }
}
 
require('Image::Imlib2')
 
var img = %s'Image::Imlib2'.new(160, 160)
img.set_color(255, 255, 255, 255) # white
img.fill_rectangle(0,0,160,160)
 
img.set_color(0,0,0,255) # black
my_draw_line(img, 10, 80, 80, 160)
my_draw_line(img, 80, 160, 160, 80)
my_draw_line(img, 160, 80, 80, 10)
my_draw_line(img, 80, 10, 10, 80)
 
img.save("test0.png")
 
# let's try the same using its internal algo
img.set_color(255, 255, 255, 255) # white
img.fill_rectangle(0,0,160,160)
img.set_color(0,0,0,255) # black
img.draw_line(10, 80, 80, 160)
img.draw_line(80, 160, 160, 80)
img.draw_line(160, 80, 80, 10)
img.draw_line(80, 10, 10, 80)
 
img.save("test1.png")
```
