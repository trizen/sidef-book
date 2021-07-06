[1]: https://rosettacode.org/wiki/Pseudorandom_number_generator_image

# [Pseudorandom number generator image][1]

```ruby
require('GD')
 
var img = %O<GD::Image>.new(500, 500, 1)
 
for y in (0..500), x in (0..500) {
    var color = img.colorAllocate(255.irand, 255.irand, 255.irand)
    img.setPixel(x, y, color)
}
 
File("image500.png").write(img.png, :raw)
```
