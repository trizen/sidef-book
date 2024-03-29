[1]: https://rosettacode.org/wiki/Conway's_Game_of_Life

# [Conway's Game of Life][1]

```ruby
var w = Num(`tput cols`)
var h = Num(`tput lines`)
var r = "\033[H"

var dirs = [[-1,-1], [-1, 0], [-1, 1], [ 0,-1],
            [ 0, 1], [ 1,-1], [ 1, 0], [ 1, 1]]

var universe = h.of { w.of {1.rand < 0.1} }

func iterate {
    var new = h.of { w.of(false) }
    static rx = (^h ~X ^w)
    for i,j in rx {
        var neighbor = 0
        for y,x in (dirs.map {|dir| dir »+« [i, j] }) {
            universe[y % h][x % w] && ++neighbor
            neighbor > 3 && break
        }
        new[i][j] = (universe[i][j]
                        ? (neighbor==2 || neighbor==3)
                        : (neighbor==3))
    }
    universe = new
}

STDOUT.autoflush(true)

loop {
    print r
    say universe.map{|row| row.map{|cell| cell ? '#' : ' '}.join }.join("\n")
    iterate()
}
```
