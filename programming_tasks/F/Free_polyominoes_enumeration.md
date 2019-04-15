[1]: https://rosettacode.org/wiki/Free_polyominoes_enumeration

# [Free polyominoes enumeration][1]

```ruby
func translate2origin(poly) {
  # Finds the min x and y coordiate of a Polyomino.
  var minx = poly.map(:head).min
  var miny = poly.map(:tail).min
  poly.map {|p| [p.head-minx, p.tail-miny] }.sort
}
 
func rotate90(x,y) { [y, -x] }
func reflect(x,y)  { [-x, y] }
 
# All the plane symmetries of a rectangular region.
func rotations_and_reflections(poly) {
    gather {
        take(poly)
        take(poly.map!{ rotate90(_...) })
        take(poly.map!{ rotate90(_...) })
        take(poly.map!{ rotate90(_...) })
        take(poly.map!{  reflect(_...) })
        take(poly.map!{ rotate90(_...) })
        take(poly.map!{ rotate90(_...) })
        take(poly.map!{ rotate90(_...) })
    }
}
 
func canonical(poly) {
  rotations_and_reflections(poly).map{|pl| translate2origin(pl) }
}
 
# All four points in Von Neumann neighborhood.
func contiguous(x, y) {
  [[x-1, y], [x+1, y], [x, y-1], [x, y+1]]
}
 
# Finds all distinct points that can be added to a Polyomino.
func new_points(poly) {
  var points = Set()
  poly.each { points << contiguous(_...)... }
  points - poly
}
 
func new_polys(polys) {
  var pattern = Set()
  polys.map { |poly|
    gather {
      new_points(poly).each { |point|
        var pl = translate2origin(poly + [point])
        next if pattern.has(pl)
        take canonical(pl).each{ pattern << _ }.min
      }
    }...
  }
}
 
# Generates polyominoes of rank n recursively.
func rank(n) {
  given (n) {
    when (0) { [[]] }
    when (1) { [[[0,0]]] }
    else     { new_polys(rank(n-1)) }
  }
}
 
# Generates a textual representation of a Polyomino.
func text_representation(poly) {
  var table = Hash()
  for x,y in (poly) { table{[x,y]} = '#' }
  var maxx = poly.map(:head).max
  var maxy = poly.map(:tail).max
  (0..maxx).map{|x| (0..maxy).map{|y| table{[x,y]} \\ ' ' }.join }
}
 
say 8.of { rank(_).len }
 
var n = (ARGV[0] ? ARGV[0].to_i : 5)
say ("\nAll free polyominoes of rank %d:" % n)
rank(n).sort.each{|poly| say text_representation(poly).join("\n")+"\n" }
```
