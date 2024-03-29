[1]: https://rosettacode.org/wiki/Ramer-Douglas-Peucker_line_simplification

# [Ramer-Douglas-Peucker line simplification][1]

```ruby
func perpendicular_distance(Arr start, Arr end, Arr point) {
    ((point == start) || (point == end)) && return 0
    var (Δx,  Δy ) = (  end »-« start)...
    var (Δpx, Δpy) = (point »-« start)...
    var h = hypot(Δx, Δy)
    [\Δx, \Δy].map { *_ /= h }
    (([Δpx, Δpy] »-« ([Δx, Δy] »*» (Δx*Δpx + Δy*Δpy))) »**» 2).sum.sqrt.round(-20)
}
 
func Ramer_Douglas_Peucker(Arr points { .all { .len > 1 } }, ε = 1) {
    points.len == 2 && return points
 
    var d = (^points -> map {
        perpendicular_distance(points[0], points[-1], points[_])
    })
 
    if (d.max > ε) {
        var i = d.index(d.max)
        return [Ramer_Douglas_Peucker(points.first(i), ε).first(-1)...,
                Ramer_Douglas_Peucker(points.slice(i), ε)...]
    }
 
    return [points[0,-1]]
}
 
say Ramer_Douglas_Peucker(
    [[0,0],[1,0.1],[2,-0.1],[3,5],[4,6],[5,7],[6,8.1],[7,9],[8,9],[9,9]]
)
```

#### Output:
```
[[0, 0], [2, -1/10], [3, 5], [7, 9], [9, 9]]
```
