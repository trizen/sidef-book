[1]: http://rosettacode.org/wiki/Heronian_triangles

# [Heronian triangles][1]

```ruby
class Triangle(a, b, c) {
 
  has (sides, perimeter, area)
 
  method init {
    sides = [a, b, c].sort
    perimeter = [a, b, c].sum
    var s = (perimeter / 2)
    area = sqrt(s * (s - a) * (s - b) * (s - c))
  }
 
  method is_valid(a,b,c) {
    var (short, middle, long) = [a, b, c].sort...
    (short + middle) > long
  }
 
  method is_heronian {
    area == area.to_i
  }
 
  method <=>(other) {
    [area, perimeter, sides] <=> [other.area, other.perimeter, other.sides]
  }
 
  method to_s {
    "%-11s%6d%8.1f" % (sides.join('x'), perimeter, area)
  }
}
 
var (max, area) = (200, 210)
var prim_triangles = []

for a in (1..max) {
  for b in (a..max) {
    for c in (b..max) {
      next if (Math.gcd(a, b, c) > 1)
      prim_triangles << Triangle(a, b, c) if Triangle.is_valid(a, b, c)
    }
  }
}
 
var sorted = prim_triangles.grep{.is_heronian}.sort
 
say "Primitive heronian triangles with sides upto #{max}: #{sorted.size}"
say "\nsides       perim.   area"
say sorted.first(10).join("\n")
say "\nTriangles with an area of: #{area}"
sorted.each{|tr| say tr if (tr.area == area)}
```

#### Output:
```
Primitive heronian triangles with sides upto 200: 517

sides       perim.   area
3x4x5          12     6.0
5x5x6          16    12.0
5x5x8          18    12.0
4x13x15        32    24.0
5x12x13        30    30.0
9x10x17        36    36.0
3x25x26        54    36.0
7x15x20        42    42.0
10x13x13       36    60.0
8x15x17        40    60.0

Triangles with an area of: 210
17x25x28       70   210.0
20x21x29       70   210.0
12x35x37       84   210.0
17x28x39       84   210.0
7x65x68       140   210.0
3x148x149     300   210.0
```
