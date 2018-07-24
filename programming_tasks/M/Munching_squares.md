[1]: https://rosettacode.org/wiki/Munching_squares

# [Munching squares][1]

```ruby
require('Imager')

var img = %O<Imager>.new(xsize => 256, ysize => 256)

for y=^256, x=^256 {
    var rgb = [(255 - x - y).abs, (255-x)^y, x^(255-y)]
    img.setpixel(x => x, y => y, color => rgb)
}

img.write(file => 'xor.png')
```

[Output image](https://github.com/trizen/rc/blob/master/img/munching-squares-sidef.png)
