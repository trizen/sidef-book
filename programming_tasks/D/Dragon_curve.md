[1]: https://rosettacode.org/wiki/Dragon_curve

# [Dragon curve][1]

Uses the LSystem class defined at [Hilbert curve](https://rosettacode.org/wiki/Hilbert_curve#Sidef).

```ruby
var rules = Hash(
    x => 'x+yF+',
    y => '-Fx-y',
)

var lsys = LSystem(
    width:  600,
    height: 600,

    xoff: -430,
    yoff: -380,

    len:   8,
    angle: 90,
    color: 'dark green',
)

lsys.execute('Fx', 11, "dragon_curve.png", rules)
```

Output image: [Dragon curve](https://github.com/trizen/rc/blob/master/img/dragon_curve-sidef.png)
