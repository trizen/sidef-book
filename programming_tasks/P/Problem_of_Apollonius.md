[1]: https://rosettacode.org/wiki/Problem_of_Apollonius

# [Problem of Apollonius][1]

```ruby
class Circle(x,y,r) {
    method to_s { "Circle(#{x}, #{y}, #{r})" }
}
 
func solve_apollonius(c, s) {
 
    var(c1, c2, c3) = c...
    var(s1, s2, s3) = s...
 
    var 𝑣11 = (2*c2.x - 2*c1.x)
    var 𝑣12 = (2*c2.y - 2*c1.y)
    var 𝑣13 = (c1.x**2 - c2.x**2 + c1.y**2 - c2.y**2 - c1.r**2 + c2.r**2)
    var 𝑣14 = (2*s2*c2.r - 2*s1*c1.r)
 
    var 𝑣21 = (2*c3.x - 2*c2.x)
    var 𝑣22 = (2*c3.y - 2*c2.y)
    var 𝑣23 = (c2.x**2 - c3.x**2 + c2.y**2 - c3.y**2 - c2.r**2 + c3.r**2)
    var 𝑣24 = (2*s3*c3.r - 2*s2*c2.r)
 
    var 𝑤12 = (𝑣12 / 𝑣11)
    var 𝑤13 = (𝑣13 / 𝑣11)
    var 𝑤14 = (𝑣14 / 𝑣11)
 
    var 𝑤22 = (𝑣22/𝑣21 - 𝑤12)
    var 𝑤23 = (𝑣23/𝑣21 - 𝑤13)
    var 𝑤24 = (𝑣24/𝑣21 - 𝑤14)
 
    var 𝑃 = (-𝑤23 / 𝑤22)
    var 𝑄 = (𝑤24 / 𝑤22)
    var 𝑀 = (-𝑤12*𝑃 - 𝑤13)
    var 𝑁 = (𝑤14 - 𝑤12*𝑄)
 
    var 𝑎 = (𝑁**2 + 𝑄**2 - 1)
    var 𝑏 = (2*𝑀*𝑁 - 2*𝑁*c1.x + 2*𝑃*𝑄 - 2*𝑄*c1.y + 2*s1*c1.r)
    var 𝑐 = (c1.x**2 + 𝑀**2 - 2*𝑀*c1.x + 𝑃**2 + c1.y**2 - 2*𝑃*c1.y - c1.r**2)
 
    var 𝐷 = (𝑏**2 - 4*𝑎*𝑐)
    var rs = ((-𝑏 - 𝐷.sqrt) / 2*𝑎)
 
    var xs = (𝑀 + 𝑁*rs)
    var ys = (𝑃 + 𝑄*rs)
 
    Circle(xs, ys, rs)
}
 
var c = [Circle(0, 0, 1), Circle(4, 0, 1), Circle(2, 4, 2)]
say solve_apollonius(c, %n<1 1 1>)
say solve_apollonius(c, %n<-1 -1 -1>)
```

#### Output:
```
Circle(2, 2.1, 3.9)
Circle(2, 0.83333333333333333333333333333333333333325, 1.166666666666666666666666666666666666667)
```
