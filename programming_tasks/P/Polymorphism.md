[1]: https://rosettacode.org/wiki/Polymorphism

# [Polymorphism][1]

```ruby
class Point(x=0, y=0) {

}

class Circle(x=0, y=0, r=0) {

}

func pp(Point obj) {
    say "Point at #{obj.x},#{obj.y}"
}

func pp(Circle obj) {
    say "Circle at #{obj.x},#{obj.y} with radius #{obj.r}"
}
```


Example:

```ruby
pp(Point.new)               # => Point at 0,0
var p = Point(1, 2)         # create a point
pp(p)                       # => Point at 1,2
say p.x                     # => 1
p.y += 1                    # add one to y
pp(p)                       # => Point at 1,3

var c = Circle(4,5,6)       # create a circle
var d = c.clone             # make a clone of it
d.r = 7.5                   # and change the radius to 7.5
pp(c)                       # => Circle at 4,5 with radius 6
pp(d)                       # => Circle at 4,5 with radius 7.5
```
