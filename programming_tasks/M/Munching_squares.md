[1]: http://rosettacode.org/wiki/Munching_squares

# [Munching squares][1]

```ruby
require 'GD';
 
var gd_img = %s'GD::Image';
var img = gd_img.new(256, 256, 1);
 
0...255 -> each { |y|
    0...255 -> each { |x|
        var color = img.colorAllocate((255 - x - y).abs, (255-x)^y, x^(255-y));
        img.setPixel(x, y, color);
    }
}
 
if (var fh = %f(xor.png).open('>:raw')) {
    fh << img.png;
}
```