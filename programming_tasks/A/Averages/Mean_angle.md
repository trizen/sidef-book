[1]: http://rosettacode.org/wiki/Averages/Mean_angle

# [Averages/Mean angle][1]

```ruby
func mean_angle(angles) {
    Math.atan2(
        angles.map { Math.sin(_ * Math.PI / 180) }.sum / angles.len,
        angles.map { Math.cos(_ * Math.PI / 180) }.sum / angles.len,
    ) * 180 / Math.PI;
}
 
[[350,10], [90,180,270,360], [10,20,30]].each { |angles|
  say "The mean angle of #{angles.dump} is: #{ '%.2f' % mean_angle(angles)} degrees";
}
```

#### Output:
```
The mean angle of [350, 10] is: 0.00 degrees
The mean angle of [90, 180, 270, 360] is: -22.96 degrees
The mean angle of [10, 20, 30] is: 20.00 degrees
```