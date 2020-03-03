[1]: https://rosettacode.org/wiki/Hilbert_curve

# [Hilbert curve][1]

Generic implementation of the Lindenmayer system:

```ruby
require('Image::Magick')

class Turtle(
    x      = 500,
    y      = 500,
    angle  = 0,
    scale  = 1,
    mirror = 1,
    xoff   = 0,
    yoff   = 0,
    color  = 'black',
) {

    has im = %O<Image::Magick>.new(size => "#{x}x#{y}")

    method init {
        angle.deg2rad!
        im.ReadImage('canvas:white')
    }

    method forward(r) {
        var (newx, newy) = (x + r*sin(angle), y + r*-cos(angle))

        im.Draw(
            primitive => 'line',
            points    => join(' ',
                           round(x    * scale + xoff),
                           round(y    * scale + yoff),
                           round(newx * scale + xoff),
                           round(newy * scale + yoff),
                        ),
            stroke      => color,
            strokewidth => 1,
        )

        (x, y) = (newx, newy)
    }

    method save_as(filename) {
        im.Write(filename)
    }

    method turn(theta) {
        angle += theta*mirror
    }

    method state {
        [x, y, angle, mirror]
    }

    method setstate(state) {
        (x, y, angle, mirror) = state...
    }

    method mirror {
        mirror.neg!
    }
}

class LSystem(
    angle  = 90,
    scale  = 1,
    xoff   = 0,
    yoff   = 0,
    len    = 5,
    color  = 'black',
    width  = 500,
    height = 500,
    turn   = 0,
) {

    has stack = []
    has table = Hash()

    has turtle = Turtle(
        x:     width,
        y:     height,
        angle: turn,
        scale: scale,
        color: color,
        xoff:  xoff,
        yoff:  yoff,
    )

    method init {

        angle.deg2rad!
        turn.deg2rad!

        table = Hash(
            '+' => { turtle.turn(angle) },
            '-' => { turtle.turn(-angle) },
            ':' => { turtle.mirror },
            '[' => { stack.push(turtle.state) },
            ']' => { turtle.setstate(stack.pop) },
        )
    }

    method execute(string, repetitions, filename, rules) {

        repetitions.times {
            string.gsub!(/(.)/, {|c| rules{c} \\ c })
        }

        string.each_char { |c|
            if (table.contains(c)) {
                table{c}.run
            }
            elsif (c.is_uppercase) {
                turtle.forward(len)
            }
        }

        turtle.save_as(filename)
    }
}
```

Generating the Hilbert curve:

```ruby
var rules = Hash(
    a => '-bF+aFa+Fb-',
    b => '+aF-bFb-Fa+',
)
 
var lsys = LSystem(
    width:  600,
    height: 600,
 
    xoff: -50,
    yoff: -50,
 
    len:   8,
    angle: 90,
    color: 'dark green',
)
 
lsys.execute('a', 6, "hilbert_curve.png", rules)
```

Output image: [Hilbert curve](https://github.com/trizen/rc/blob/master/img/hilbert-curve-sidef.png)
