[1]: https://rosettacode.org/wiki/Averages/Mean_angle

# [Averages/Mean angle][1]

```ruby
func mean_angle(angles) {
    atan2(
        Math.avg(angles.map{ .deg2rad.sin }...),
        Math.avg(angles.map{ .deg2rad.cos }...),
    ) -> rad2deg;
}

[[350,10], [90,180,270,360], [10,20,30]].each { |angles|
  say "The mean angle of #{angles.dump} is: #{ '%.2f' % mean_angle(angles)} degrees";
}
```

#### Output:
```
The mean angle of [350, 10] is: 0.00 degrees
The mean angle of [90, 180, 270, 360] is: -90.00 degrees
The mean angle of [10, 20, 30] is: 20.00 degrees
```
