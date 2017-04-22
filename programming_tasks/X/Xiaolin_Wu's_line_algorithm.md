[1]: http://rosettacode.org/wiki/Xiaolin_Wu's_line_algorithm

# [Xiaolin Wu's line algorithm][1]

```ruby
func plot(x, y, c) {
    c && printf("plot %d %d %.1f\n", x, y, c)
}
 
func fpart(x) {
    x - int(x)
}
 
func rfpart(x) {
    1 - fpart(x)
}
 
func drawLine(x0, y0, x1, y1) {
 
    var p = plot
    if (abs(y1 - y0) > abs(x1 - x0)) {
        p = {|arg| plot(arg[1, 0, 2]) }
        (x0, y0, x1, y1) = (y0, x0, y1, x1)
    }
 
    if (x0 > x1) {
        (x0, x1, y0, y1) = (x1, x0, y1, y0)
    }
 
    var dx = (x1 - x0)
    var dy = (y1 - y0)
    var gradient = (dy / dx)
 
    var xends = []
    var intery
 
    # handle the endpoints
    for x,y in [[x0, y0], [x1, y1]] {
        var xend = int(x + 0.5)
        var yend = (y + gradient*(xend-x))
        var xgap = rfpart(x + 0.5)
 
        var x_pixel = xend
        var y_pixel = yend.int
        xends << x_pixel
 
        p.call(x_pixel, y_pixel  , rfpart(yend) * xgap)
        p.call(x_pixel, y_pixel+1,  fpart(yend) * xgap)
        defined(intery) && next
 
        # first y-intersection for the main loop
        intery = (yend + gradient)
    }
 
    # main loop
    for x in (xends[0]+1 .. xends[1]-1) {
        p.call(x, intery.int,  rfpart(intery))
        p.call(x, intery.int+1, fpart(intery))
        intery += gradient
    }
}
 
drawLine(0, 1, 10, 2)
```

#### Output:
```
plot 0 1 0.5
plot 10 2 0.5
plot 1 1 0.9
plot 1 2 0.1
plot 2 1 0.8
plot 2 2 0.2
plot 3 1 0.7
plot 3 2 0.3
plot 4 1 0.6
plot 4 2 0.4
plot 5 1 0.5
plot 5 2 0.5
plot 6 1 0.4
plot 6 2 0.6
plot 7 1 0.3
plot 7 2 0.7
plot 8 1 0.2
plot 8 2 0.8
plot 9 1 0.1
plot 9 2 0.9
```
