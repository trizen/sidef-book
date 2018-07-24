[1]: https://rosettacode.org/wiki/Archimedean_spiral

# [Archimedean spiral][1]

```ruby
require('Imager')
define π = Num.pi
 
var (w, h) = (400, 400)
var img = %O<Imager>.new(xsize => w, ysize => h)
 
for Θ in (0 .. 52*π -> by(0.025)) {
    img.setpixel(
        x => floor(cos(Θ / π)*Θ + w/2),
        y => floor(sin(Θ / π)*Θ + h/2),
        color => [255, 0, 0]
    )
}
 
img.write(file => 'Archimedean_spiral.png')
```

[Output image](https://github.com/trizen/rc/blob/master/img/archimedean-spiral-sidef.png)
