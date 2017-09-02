[1]: https://rosettacode.org/wiki/Elliptic_curve_arithmetic

# [Elliptic curve arithmetic][1]

```ruby
module EC {
 
    var A = 0
    var B = 7
 
    class Horizon {
        method to_s {
            "EC Point at horizon"
        }
 
        method *(_) {
            self
        }
 
        method -(_) {
            self
        }
    }
 
    class Point(Number x, Number y) {
        method to_s {
            "EC Point at x=#{x}, y=#{y}"
        }
 
        method neg {
            Point(x, -y)
        }
 
        method -(Point p) {
            self + -p
        }
 
        method +(Point p) {
 
            if (x == p.x) {
                return (y == p.y ? self*2 : Horizon())
            }
            else {
                var slope = (p.y - y)/(p.x - x)
                var x2 = (slope**2 - x - p.x)
                var y2 = (slope * (x - x2) - y)
                Point(x2, y2)
            }
        }
 
        method +(Horizon _) {
            self
        }
 
        method *((0)) {
            Horizon()
        }
 
        method *((1)) {
            self
        }
 
        method *((2)) {
            var l = (3 * x**2 + A)/(2 * y)
            var x2 = (l**2 - 2*x)
            var y2 = (l * (x - x2) - y)
            Point(x2, y2)
        }
 
        method *(Number n) {
            2*(self * (n>>1)) + self*(n % 2)
        }
    }
 
    class Horizon {
        method +(Point p) {
            p
        }
    }
 
    class Number {
        method +(Point p) {
            p + self
        }
        method *(Point p) {
            p * self
        }
        method *(Horizon h) {
            h
        }
        method -(Point p) {
            -p + self
        }
    }
}
 
say var p = with(1) {|v| EC::Point(v, sqrt(abs(1 - v**3 - EC::A*v - EC::B))) }
say var q = with(2) {|v| EC::Point(v, sqrt(abs(1 - v**3 - EC::A*v - EC::B))) }
say var s = (p + q)
 
say ("checking alignment:  ", abs((p.x - q.x)*(-s.y - q.y) - (p.y - q.y)*(s.x - q.x)) < 1e-20)
```

#### Output:
```
EC Point at x=1, y=2.64575131106459059050161575363926042571025918308
EC Point at x=2, y=3.74165738677394138558374873231654930175601980778
EC Point at x=-1.79898987322333068322364213893577309997540625528, y=0.421678696849803028974882458314430376814790014487
checking alignment:  true
```