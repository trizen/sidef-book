[1]: http://rosettacode.org/wiki/Spiral_matrix

# [Spiral matrix][1]

```ruby
func spiral(n) {
    var (x, y, dx, dy, a) = (0, 0, 1, 0, [])
    { |i|
        a[y][x] = i
        var (nx, ny) = (x+dx, y+dy)
        (  if (dx ==  1 && (nx == n || a[ny][nx]!=nil)) { [ 0,  1] }
        elsif (dy ==  1 && (ny == n || a[ny][nx]!=nil)) { [-1,  0] }
        elsif (dx == -1 && (nx  < 0 || a[ny][nx]!=nil)) { [ 0, -1] }
        elsif (dy == -1 && (ny  < 0 || a[ny][nx]!=nil)) { [ 1,  0] }
        else                                            { [dx, dy] }
        ) » (\dx, \dy)
        x = x+dx
        y = y+dy
    } << (1 .. n**2)
    return a
}
 
spiral(5).each { |row|
    row.map {"%3d" % _}.join(' ').say
}
```

#### Output:
```
  1   2   3   4   5
 16  17  18  19   6
 15  24  25  20   7
 14  23  22  21   8
 13  12  11  10   9
```
