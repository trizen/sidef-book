[1]: http://rosettacode.org/wiki/Draw_a_cuboid

# [Draw a cuboid][1]

```ruby
var DIR = Hash.new("-" => [1,0], "|" => [0,1], "/" => [1,1]);
 
func cuboid(nx, ny, nz) {
  say("cuboid %d %d %d:" % [nx, ny, nz]);
  var(x, y, z) = (8*nx, 2*ny, 4*nz);
  var area = [];
  var line = func(n, sx, sy, c) {
    var(dx, dy) = DIR{c}...;
    0..n -> each {|i|
      var (xi, yi) = (sx + i*dx, sy + i*dy);
      area[yi] \\= [" "]*(x+y+1);
      area[yi][xi] = (area[yi][xi] == " " ? c : '+');
    };
  };
 
  0 .. nz-1 -> each {|i| line.call(x,       0,     4*i, "-")};
  0 .. ny   -> each {|i| line.call(x,     2*i, z + 2*i, "-")};
  0 .. nx-1 -> each {|i| line.call(z,     8*i,       0, "|")};
  0 .. ny   -> each {|i| line.call(z, x + 2*i,     2*i, "|")};
  0 .. nz-1 -> each {|i| line.call(y,       x,     4*i, "/")};
  0 .. nx   -> each {|i| line.call(y,     8*i,       z, "/")};
 
  area.reverse.each { |line|
     say line.join('');
  };
}
 
cuboid(2, 3, 4);
cuboid(1, 1, 1);
cuboid(6, 2, 1);
cuboid(2, 4, 1);
```


*A faster approach:*

```ruby
func cuboid (x=1,y=1,z=1,s=' ',c='+',h='-',v='|',d='/') {
    say("cuboid %d %d %d:" % [x, y, z]);
    ' ' * z+1 + c + h*x + c -> say;
 
    { |i|
        ' ' * (z - i + 1) + d + s*x + d +
              (s * (i - (i > y ? i-y : 1))) +
              (i - 1 == y ? c : (i > y ? d : v)) -> say
    } * z;
 
    c + h*x + c + (s * (z < y ? z : y) +
        (z < y ? v : (z == y ? c : d))) -> say;
 
    { |i|
        v + s*x + v + (z > y
            ? (i >= z ? (s*x + c) : (s * y-i + d))
            : (y - i > z
                ? (s * z + v)
                : (s * y-i + (y-i == z ? c : d))
               )
        ) -> say;
    } * y;
 
    c + h*x + c -> say;
};
 
cuboid(2, 3, 4);
cuboid(1, 1, 1);
cuboid(6, 2, 1);
cuboid(2, 4, 1);
```

#### Output:
```
cuboid 2 3 4:
     +--+
    /  /|
   /  / |
  /  /  |
 /  /   +
+--+   /
|  |  /
|  | /
|  |/
+--+
cuboid 1 1 1:
  +-+
 / /|
+-+ +
| |/
+-+
cuboid 6 2 1:
  +------+
 /      /|
+------+ |
|      | +
|      |/
+------+
cuboid 2 4 1:
  +--+
 /  /|
+--+ |
|  | |
|  | |
|  | +
|  |/
+--+
```