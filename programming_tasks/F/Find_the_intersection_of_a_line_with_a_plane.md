[1]: https://rosettacode.org/wiki/Find_the_intersection_of_a_line_with_a_plane

# [Find the intersection of a line with a plane][1]

```ruby
struct Line {
    P0,       # point
    u⃗,        # ray
}
 
struct Plane {
    V0,       # point
    n⃗,        # normal
}
 
func dot_prod(a, b) { a »*« b -> sum }
 
func line_plane_intersection(𝑳, 𝑷) {
    var cos = dot_prod(𝑷.n⃗, 𝑳.u⃗) ->
     || return 'Vectors are orthogonal'
    var 𝑊 = (𝑳.P0 »-« 𝑷.V0)
    var S𝐼 = -(dot_prod(𝑷.n⃗, 𝑊) / cos)
    𝑊 »+« (𝑳.u⃗ »*» S𝐼) »+« 𝑷.V0
}
 
say ('Intersection at point: ', line_plane_intersection(
         Line(P0: [0,0,10], u⃗: [0,-1,-1]),
        Plane(V0: [0,0, 5], n⃗: [0, 0, 1]),
))
```

#### Output:
```
Intersection at point: [0, -5, 5]
```