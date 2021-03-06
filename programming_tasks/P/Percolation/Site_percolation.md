[1]: https://rosettacode.org/wiki/Percolation/Site_percolation

# [Percolation/Site percolation][1]

```ruby
class Percolate {
 
    has block = '▒'
    has water = '+'
    has pore  = ' '
    has grid  = 15
    has site  = []
 
    enum <DeadEnd, Up, Right, Down, Left>
 
    method direction(x, y) {
        ((site[y + 1][x] == pore) && Down ) ||
        ((site[y][x - 1] == pore) && Left ) ||
        ((site[y][x + 1] == pore) && Right) ||
        ((site[y - 1][x] == pore) && Up   ) ||
        DeadEnd
    }
 
    method move(dir, x, y) {
        given (dir) {
            when (Up)    { site[--y][x] = water }
            when (Down)  { site[++y][x] = water }
            when (Left)  { site[y][--x] = water }
            when (Right) { site[y][++x] = water }
        }
        return (x, y)
    }
 
    method percolate (prob  = 0.6) {
        site[0] = grid.of(pore)
        site[grid + 1] = grid.of(pore)
 
        for x = ^grid, y = 1..grid {
            site[y][x] = (1.rand < prob ? pore : block)
        }
 
        site[0][0] = water
 
        var stack = []
        var (x, y) = (0, 0)
 
        loop {
            if (var dir = self.direction(x, y)) {
                stack << [x, y]
                (x,y) = self.move(dir, x, y)
            }
            else {
                stack || return 0
                (x,y) = stack.pop...
            }
            return 1 if (y > grid)
        }
    }
}
 
var obj = Percolate()
say 'Sample percolation at 0.6'
obj.percolate(0.6)
obj.site.each { .join.say }
say ''
 
var tests = 100
say "Doing #{tests} trials at each porosity:"
for p in (0.1..1 `by` 0.1) {
    printf("p = %0.1f: %0.3f\n", p, tests.of { obj.percolate(p) }.sum / tests)
}
```

#### Output:
```
Sample percolation at 0.6
+              
+    ▒▒▒  ▒ ▒▒ 
+  ▒  ▒   ▒ ▒  
++++  ▒  ▒    ▒
▒+▒+++++    ▒ ▒
 ▒ ▒▒▒▒+       
▒▒ ▒ ▒ +      ▒
▒     ▒+++ ▒  ▒
  ▒ ▒ ▒+▒+  ▒  
▒ ▒    ▒ + ▒  ▒
 ▒   ▒ +++   ▒▒
▒▒▒ ▒▒▒+▒+▒ ▒ ▒
▒   ▒▒ + ▒    ▒
 ▒▒  ▒▒+++  ▒ ▒
     ▒ ▒▒+     
▒   ▒ ▒  +     
         +     

Doing 100 trials at each porosity:
p = 0.1: 0.000
p = 0.2: 0.000
p = 0.3: 0.000
p = 0.4: 0.020
p = 0.5: 0.090
p = 0.6: 0.570
p = 0.7: 0.930
p = 0.8: 1.000
p = 0.9: 1.000
p = 1.0: 1.000
```