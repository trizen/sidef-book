[1]: https://rosettacode.org/wiki/Langton's_ant

# [Langton's ant][1]

```ruby
define dirs = [[1,0], [0,-1], [-1,0], [0,1]]
define size = 100

enum |White, Black|
var plane = size.of { size.of (White) }

var (x, y) = ([size >> 1] * 2)...
var dir = dirs.len.irand

var moves = 0
loop {
    (x >= 0) && (y >= 0) && (x < size) && (y < size) || break

    given (plane[x][y]) {
        when (White) { dir--; plane[x][y] = Black }
        when (Black) { dir++; plane[x][y] = White }
    }

    ++moves
    [[\x, \y], dirs[dir %= dirs.len]].zip {|a,b| *a += b }
}

say "Out of bounds after #{moves} moves at (#{x}, #{y})"
plane.map{.map {|square| square == Black ? '#' : '.' }}.each{.join.say}
```
