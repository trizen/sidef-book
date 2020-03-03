[1]: https://rosettacode.org/wiki/Peano_curve

# [Peano curve][1]

Uses the LSystem class defined at [Hilbert curve](https://rosettacode.org/wiki/Hilbert_curve#Sidef).

```ruby
var rules = Hash(
    l => 'lFrFl-F-rFlFr+F+lFrFl',
    r => 'rFlFr+F+lFrFl-F-rFlFr',
)

var lsys = LSystem(
    width:  500,
    height: 500,

    xoff: -50,
    yoff: -50,

    len:   5,
    angle: 90,
    color: 'dark green',
)

lsys.execute('l', 4, "peano_curve.png", rules)
```


Output image: [Peano curve](https://github.com/trizen/rc/blob/master/img/peano_curve-sidef.png)
