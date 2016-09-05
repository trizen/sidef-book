[1]: http://rosettacode.org/wiki/Chaos_game

# [Chaos game][1]

```ruby
require('Imager')
 
var width  = 600
var height = 600
 
var points = [
    [width//2,        0],
    [       0, height-1],
    [height-1, height-1],
]
 
var img = %s|Imager|.new(
                      xsize => width,
                      ysize => height,
                     )
 
var color = %s|Imager::Color|.new('#ff0000')
var r = [width.irand, height.irand]
 
30000.times {
    var p = points.rand
 
    r[] = (
        (p[0] + r[0]) // 2,
        (p[1] + r[1]) // 2,
    )
 
    img.setpixel(
        x     => r[0],
        y     => r[1],
        color => color,
    )
}
 
img.write(file => 'chaos_game.png')
```