[1]: https://rosettacode.org/wiki/Koch_curve

# [Koch curve][1]

Using the LSystem class defined at [Hilbert curve](https://rosettacode.org/wiki/Hilbert_curve#Sidef).

```ruby
var rules = Hash(
    F => 'F+F--F+F',
)
 
var lsys = LSystem(
    width:  800,
    height: 800,
 
    xoff: -210,
    yoff: -90,
 
    len:   8,
    angle: 60,
    color: 'dark green',
)
 
lsys.execute('F--F--F', 4, "koch_snowflake.png", rules)
```

[Output image](https://github.com/trizen/rc/blob/master/img/koch-snowflake-sidef.png)
