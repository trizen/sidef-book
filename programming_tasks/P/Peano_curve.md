[1]: https://rosettacode.org/wiki/Peano_curve

# [Peano curve][1]

Using the LSystem class defined at [Hilbert curve](https://rosettacode.org/wiki/Hilbert_curve#Sidef).

```ruby
var rules = Hash(
    L => 'LFRFL-F-RFLFR+F+LFRFL',
    R => 'RFLFR+F+LFRFL-F-RFLFR',
)
 
var lsys = LSystem(
    width:  325,
    height: 650,
 
    xoff: -3,
    yoff: -3,
 
    len:   4,
    angle: 90,
    color: 'dark green',
)
 
lsys.execute('L', 4, "peano_curve.png", rules)
```


Output image: [Peano curve](https://github.com/trizen/rc/blob/master/img/peano_curve.png)
