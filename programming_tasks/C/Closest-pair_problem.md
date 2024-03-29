[1]: https://rosettacode.org/wiki/Closest-pair_problem

# [Closest-pair problem][1]

```ruby
func dist_squared(a, b) {
    sqr(a[0] - b[0]) + sqr(a[1] - b[1])
}

func closest_pair_simple(arr) {
    arr.len < 2 && return Inf
    var (a, b, d) = (arr[0, 1], dist_squared(arr[0,1]))
    arr.clone!
    while (arr) {
        var p = arr.pop
        for l in arr {
            var t = dist_squared(p, l)
            if (t < d) {
                (a, b, d) = (p, l, t)
            }
        }
    }
    return(a, b, d.sqrt)
}

func closest_pair_real(rx, ry) {
    rx.len <= 3 && return closest_pair_simple(rx)

    var N = rx.len
    var midx = (ceil(N/2)-1)
    var (PL, PR) = rx.part(midx)

    var xm = rx[midx][0]

    var yR = []
    var yL = []

    for item in ry {
        (item[0] <= xm ? yR : yL) << item
    }

    var (al, bl, dL) = closest_pair_real(PL, yR)
    var (ar, br, dR) = closest_pair_real(PR, yL)

    al == Inf && return (ar, br, dR)
    ar == Inf && return (al, bl, dL)

    var (m1, m2, dmin) = (dR < dL ? [ar, br, dR]...
                                  : [al, bl, dL]...)

    var yS = ry.grep { |a| abs(xm - a[0]) < dmin }

    var (w1, w2, closest) = (m1, m2, dmin)
    for i in (0 ..^ yS.end) {
        for k in (i+1 .. yS.end) {
            yS[k][1] - yS[i][1] < dmin || break
            var d = dist_squared(yS[k], yS[i]).sqrt
            if (d < closest) {
                (w1, w2, closest) = (yS[k], yS[i], d)
            }
        }
    }

    return (w1, w2, closest)
}

func closest_pair(r) {
    var ax = r.sort_by { |a| a[0] }
    var ay = r.sort_by { |a| a[1] }
    return closest_pair_real(ax, ay);
}

var N = 100
var points = N.of { [1.rand*20 - 10, 1.rand*20 - 10] }
var (af, bf, df) = closest_pair(points)
say "#{df} at (#{af.join(' ')}), (#{bf.join(' ')})"
```
