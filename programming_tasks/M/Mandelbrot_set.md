[1]: https://rosettacode.org/wiki/Mandelbrot_set

# [Mandelbrot set][1]

```ruby
func mandelbrot(z) {
    var c = z
    {   z = (z*z + c)
        z.abs > 2 && return true
    } * 20
    return false
}
 
for y range(1, -1, -0.05) {
    for x in range(-2, 0.5, 0.0315) {
        print(mandelbrot(x + y.i) ? ' ' : '#')
    }
    print "\n"
}
```
