[1]: https://rosettacode.org/wiki/Draw_a_sphere

# [Draw a sphere][1]

Produces a PGM image.

```ruby
func normalize (vec)  { vec »/» (vec »*« vec -> sum.sqrt) }
func dot       (x, y) { -(x »*« y -> sum) `max` 0 }
 
var x = var y = 255
x += 1 if x.is_even    # must be odd
 
var light = normalize([ 3, 2, -5 ])
var depth = 255
 
func draw_sphere(rad, k, ambient) {
    var pixels = []
    var r2 = (rad * rad)
    var range = (-rad .. rad)
    for x,y in (range ~X range) {
        if ((var x2 = x*x) + (var y2 = y*y) < r2) {
            var vector = normalize([x, y, (r2 - x2 - y2).sqrt])
            var intensity = (dot(light, vector)**k + ambient)
            var pixel = (0 `max` (intensity*depth -> int) `min` depth)
            pixels << pixel
        }
        else {
            pixels << 0
        }
    }
    return pixels
}
 
var outfile = %f'sphere-sidef.pgm'
var out = outfile.open('>:raw')
 
out.say("P5\n#{x} #{y}\n#{depth}")    # .pgm header
out.print(draw_sphere((x-1)/2, .9, .2).map{.chr}.join)
out.close
```
