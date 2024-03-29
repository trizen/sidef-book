[1]: https://rosettacode.org/wiki/Kronecker_product_based_fractals

# [Kronecker product based fractals][1]

```ruby
func kronecker_product (a, b) { a ~X b -> map { _[0] ~X* _[1] } }
 
func kronecker_fractal(pattern, order=4) {
    var kronecker = pattern
    { kronecker = kronecker_product(kronecker, pattern) } * order
    return kronecker
}
 
var vicsek = [[0,1,0], [1,1,1], [0,1,0]]
var carpet = [[1,1,1], [1,0,1], [1,1,1]]
var six    = [[0,1,1,1,0], [1,0,0,0,1], [1,0,0,0,0],
              [1,1,1,1,0], [1,0,0,0,1], [1,0,0,0,1], [0,1,1,1,0]]
 
require("Imager")
 
for name,shape,order in [
    [:vicsek, vicsek, 4],
    [:carpet, carpet, 4],
    [:six,    six,    3],
] {
    var pat = kronecker_fractal(shape, order)
    var img = %O<Imager>.new(xsize => pat[0].len, ysize => pat.len)
    for x,y in (^pat[0].len ~X ^pat.len) {
        img.setpixel(x => x, y => y, color => (pat[y][x] ? <255 255 32> : <16 16 16>))
    }
    img.write(file => "kronecker-#{name}-sidef.png")
}
```

### Output images:

    * [Kronecker six](https://github.com/trizen/rc/blob/master/img/kronecker-six-sidef.png)
    * [Kronecker carpet](https://github.com/trizen/rc/blob/master/img/kronecker-carpet-sidef.png)
    * [Kronecker vicsek](https://github.com/trizen/rc/blob/master/img/kronecker-vicsek-sidef.png)
