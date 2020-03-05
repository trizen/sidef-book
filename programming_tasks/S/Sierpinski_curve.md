[1]: https://rosettacode.org/wiki/Sierpinski_curve

# [Sierpinski curve][1]

Uses the **LSystem()** class from [Hilbert curve](https://rosettacode.org/wiki/Hilbert_curve#Sidef).

```ruby
var rules = Hash(
    x => 'xF+G+xF--F--xF+G+x',
)
 
var lsys = LSystem(
    width:  550,
    height: 550,
 
    xoff: -9,
    yoff: -271,
 
    len:   5,
    angle: 45,
    color: 'dark green',
)
 
lsys.execute('F--xF--F--xF', 5, "sierpiński_curve.png", rules)
```


Output image: [Sierpiński curve](https://github.com/trizen/rc/blob/master/img/sierpi%C5%84ski_curve-sidef.png)
