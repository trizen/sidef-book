[1]: https://rosettacode.org/wiki/Colour_bars/Display

# [Colour bars/Display][1]

```ruby
require('GD')
 
var colors = Hash(
              white   => [255, 255, 255],
              red     => [255, 0,   0],
              green   => [0,   255, 0],
              blue    => [0,   0,   255],
              magenta => [255, 0,   255],
              yellow  => [255, 255, 0],
              cyan    => [0,   255, 255],
              black   => [0,   0,   0],
             )
 
var barwidth = 160/8
var image    = %O<GD::Image>.new(160, 100)
var start    = 0
 
colors.values.each { |rgb|
    var paintcolor = image.colorAllocate(rgb...)
    image.filledRectangle(start * barwidth, 0, start*barwidth + barwidth - 1, 99, paintcolor)
    start++
}

%f'colorbars.png'.open('>:raw').print(image.png)
```
