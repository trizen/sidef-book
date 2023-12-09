[1]: https://rosettacode.org/wiki/Orbital_elements

# [Orbital elements][1]

```ruby
func orbital_state_vectors(
    semimajor_axis,
    eccentricity,
    inclination,
    longitude_of_ascending_node,
    argument_of_periapsis,
    true_anomaly
) {

    var (i, j, k) = (
        Vector(1, 0, 0),
        Vector(0, 1, 0),
        Vector(0, 0, 1),
    )

    func muladd(v1, x1, v2, x2) {
        (v1 * x1) + (v2 * x2)
    }

    func rotate(Ref i, Ref j, α) {
        (*i, *j) = (
            muladd(*i, +cos(α), *j, sin(α)),
            muladd(*i, -sin(α), *j, cos(α)),
        )
    }

    rotate(\i, \j, longitude_of_ascending_node)
    rotate(\j, \k, inclination)
    rotate(\i, \j, argument_of_periapsis)

    var l = (eccentricity == 1 ? 2*semimajor_axis
                               : semimajor_axis*(1 - eccentricity**2))

    var (c, s) = with(true_anomaly) { (.cos, .sin) }

    var r = l/(1 + eccentricity*c)
    var rprime = (s * r**2 / l)
    var position = muladd(i, c, j, s)*r

    var speed = muladd(i, rprime*c - r*s, j, rprime*s + r*c)
    speed /= speed.abs
    speed *= sqrt(2/r - 1/semimajor_axis)

    struct Result { position, speed }
    Result(position, speed)
}

for args in ([
    [1, 0.1, 0, 355/(113*6), 0, 0],
    [1, 0.1, Num.pi/18, Num.pi/6, Num.pi/4, 0]
]) {
    var r = orbital_state_vectors(args...)

    say "Arguments: #{args}:"
    say "Position : #{r.position}"
    say "Speed    : #{r.speed}\n"
}
```

#### Output:
```
Arguments: [1, 1/10, 0, 355/678, 0, 0]:
Position : Vector(0.779422843398679832042176328223663037464703527986, 0.450000034653684237432302249506712706822033851071, 0)
Speed    : Vector(-0.552770840960443759673279062314259546277084494097, 0.957427083179761535246200368614952095349966503287, 0)

Arguments: [1, 1/10, 0.174532925199432957692369076848861271344287188854, 0.523598775598298873077107230546583814032861566563, 0.785398163397448309615660845819875721049292349844, 0]:
Position : Vector(0.23777128398220654779107184959165027147748809404, 0.860960261697715834668966272382699039216399966872, 0.110509023572075562109405412890808505271310143909)
Speed    : Vector(-1.06193301748006004757467368094494935655538772696, 0.275850020569249507846452830330085489348356659642, 0.135747024865598167166145512759280712986072818844)

```
