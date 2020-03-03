[1]: https://rosettacode.org/wiki/Sierpinski_arrowhead_curve

# [Sierpinski arrowhead curve][1]

Uses the **LSystem()** class from [Hilbert curve](https://rosettacode.org/wiki/Hilbert_curve#Sidef).

```ruby
var rules = Hash(
    x => 'yF+xF+y',
    y => 'xF-yF-x',
)
 
var lsys = LSystem(
    width:  550,
    height: 500,
 
    xoff: -20,
    yoff: -30,
 
    len:   4,
    turn: -90,
    angle: 60,
    color: 'dark green',
)
 
lsys.execute('xF', 7, "sierpiński_arrowhead.png", rules)
```


Output image: [Sierpiński arrowhead](https://github.com/trizen/rc/blob/master/img/sierpi%C5%84ski_arrowhead-sidef.png)
