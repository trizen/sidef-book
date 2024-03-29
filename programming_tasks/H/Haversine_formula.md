[1]: https://rosettacode.org/wiki/Haversine_formula

# [Haversine formula][1]

```ruby
class EarthPoint(lat, lon) {

    const earth_radius = 6371       # mean earth radius
    const radian_ratio = Num.pi/180

    # accessors for radians
    method latR { self.lat * radian_ratio }
    method lonR { self.lon * radian_ratio }

    method haversine_dist(EarthPoint p) {
        var arc = EarthPoint(
              self.lat - p.lat,
              self.lon - p.lon,
        )

        var a = Math.sum(
                  (arc.latR / 2).sin**2,
                  (arc.lonR / 2).sin**2 *
                    self.latR.cos * p.latR.cos
                )

        earth_radius * a.sqrt.asin * 2
    }
}

var BNA = EarthPoint.new(lat: 36.12, lon: -86.67)
var LAX = EarthPoint.new(lat: 33.94, lon: -118.4)

say BNA.haversine_dist(LAX)   #=> 2886.444442837983299747157823945746716...
```
