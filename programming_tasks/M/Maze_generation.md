[1]: https://rosettacode.org/wiki/Maze_generation

# [Maze generation][1]

```ruby
var(w:5, h:5) = ARGV.map{.to_i}...
var avail = (w * h)

# cell is padded by sentinel col and row, so I don't check array bounds
var cell = (1..h -> map {([true] * w) + [false]} + [[false] * w+1])
var ver  = (1..h -> map {["|  "] * w })
var hor  = (0..h -> map {["+--"] * w })

func walk(x, y) {
    cell[y][x] = false
    avail-- > 0 || return nil   # no more cells

    var d = [[-1, 0], [0, 1], [1, 0], [0, -1]]
    while (!d.is_empty) {
        var i = d.pop_rand
        var (x1, y1) = (x + i[0], y + i[1])

        cell[y1][x1] || next

        if (x == x1) { hor[[y1, y].max][x] = '+  ' }
        if (y == y1) { ver[y][[x1, x].max] = '   ' }
        walk(x1, y1)
    }
}

walk(w.rand.int, h.rand.int)   # generate

for i in (0 .. h) {
    say (hor[i].join('') + '+')
    if (i < h) {
        say (ver[i].join('') + '|')
    }
}
```

#### Output:
```
+--+--+--+--+--+
|           |  |
+--+  +--+  +  +
|     |        |
+  +--+--+--+--+
|     |        |
+--+  +  +--+  +
|     |  |     |
+  +--+--+  +--+
|              |
+--+--+--+--+--+
```
