[1]: https://rosettacode.org/wiki/Grayscale_image

# [Grayscale image][1]

```ruby
require('Image::Imlib2')

func tograyscale(img) {
    var (width, height) = (img.width, img.height)
    var gimg = %O<Image::Imlib2>.new(width, height)
    for y,x in (^height ~X ^width) {
        var (r, g, b) = img.query_pixel(x, y)
        var gray = int(0.2126*r + 0.7152*g + 0.0722*b)
        gimg.set_color(gray, gray, gray, 255)
        gimg.draw_point(x, y)
    }
    return gimg
}

var (input='input.png', output='output.png') = ARGV...
var image = %O<Image::Imlib2>.load(input)
var gscale = tograyscale(image)
gscale.set_quality(80)
gscale.save(output)
```
