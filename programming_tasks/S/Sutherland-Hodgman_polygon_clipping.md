[1]: https://rosettacode.org/wiki/Sutherland-Hodgman_polygon_clipping

# [Sutherland-Hodgman polygon clipping][1]

```ruby
class Point(x, y) {
    method to_s {
        "(#{'%.2f' % x}, #{'%.2f' % y})"
    }
}
 
func sutherland_hodgman(subjectPolygon, clipPolygon) {
  var inside = { |cp1, cp2, p|
    ((cp2.x-cp1.x)*(p.y-cp1.y)) > ((cp2.y-cp1.y)*(p.x-cp1.x))
  }
 
  var intersection = { |cp1, cp2, s, e|
    var (dcx, dcy) = (cp1.x-cp2.x, cp1.y-cp2.y)
    var (dpx, dpy) = (s.x-e.x, s.y-e.y)
    var n1 = (cp1.x*cp2.y - cp1.y*cp2.x)
    var n2 = (s.x*e.y - s.y*e.x)
    var n3 = (1 / (dcx*dpy - dcy*dpx))
    Point((n1*dpx - n2*dcx) * n3, (n1*dpy - n2*dcy) * n3)
  }
 
  var outputList = subjectPolygon
  var cp1 = clipPolygon.last
  for cp2 in clipPolygon {
    var inputList = outputList
    outputList = []
    var s = inputList.last
    for e in inputList {
      if (inside(cp1, cp2, e)) {
        outputList << intersection(cp1, cp2, s, e) if !inside(cp1, cp2, s)
        outputList << e
      }
      elsif(inside(cp1, cp2, s)) {
        outputList << intersection(cp1, cp2, s, e)
      }
      s = e
    }
    cp1 = cp2
  }
  outputList
}
 
var subjectPolygon = [
    [50,  150], [200,  50], [350, 150], [350, 300],
    [250, 300], [200, 250], [150, 350], [100, 250],
    [100, 200]
].map{|pnt| Point(pnt...) }
 
var clipPolygon = [
    [100, 100], [300, 100],
    [300, 300], [100, 300]
].map{|pnt| Point(pnt...) }
 
sutherland_hodgman(subjectPolygon, clipPolygon).each { .say }
```

#### Output:
```
(100.00, 116.67)
(125.00, 100.00)
(275.00, 100.00)
(300.00, 116.67)
(300.00, 300.00)
(250.00, 300.00)
(200.00, 250.00)
(175.00, 300.00)
(125.00, 300.00)
(100.00, 250.00)
```