[1]: https://rosettacode.org/wiki/Sierpinski_square_curve

# [Sierpinski square curve][1]

Uses the **LSystem()** class from [Hilbert curve](https://rosettacode.org/wiki/Hilbert_curve#Sidef).

```ruby
var rules = Hash(
    x => 'xF-F+F-xF+F+xF-F+F-x',
)
 
var lsys = LSystem(
    width:  510,
    height: 510,
 
    xoff: -505,
    yoff: -254,
 
    len:   4,
    angle: 90,
    color: 'dark green',
)
 
lsys.execute('F+xF+F+xF', 5, "sierpiński_square_curve.png", rules)
```


Output image: [Sierpiński square curve](https://github.com/trizen/rc/blob/master/img/sierpi%C5%84ski_square_curve-sidef.png)
