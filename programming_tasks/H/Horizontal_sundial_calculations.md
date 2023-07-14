[1]: https://rosettacode.org/wiki/Horizontal_sundial_calculations

# [Horizontal sundial calculations][1]

```ruby
var latitude  = read('Enter latitude       => ', Number)
var longitude = read('Enter longitude      => ', Number)
var meridian  = read('Enter legal meridian => ', Number)
 
var lat_sin = latitude.deg2rad.sin
var offset = (meridian - longitude)
 
say('Sine of latitude: ', "%.4f" % lat_sin)
say('Longitude offset: ', offset)
say('=' * 48)
say(' Hour  : Sun hour angle° : Dial hour line angle°')
 
for hour in range(-6, 6) {
    var sun_deg  = (15*hour + offset)
    var line_deg = rad2deg(
        atan2(
            sin(deg2rad(sun_deg)) * lat_sin,
            cos(deg2rad(sun_deg))
        )
    )
    printf("%2d %s      %7.3f             %7.3f\n",
      (hour + 12) % 12 || 12, (hour < 0 ? 'AM' : 'PM'), sun_deg, line_deg)
}
```

#### Output:
```
Enter latitude       => -4.95
Enter longitude      => -150.5
Enter legal meridian => -150
Sine of latitude: -0.0863
Longitude offset: 0.5
================================================
 Hour  : Sun hour angle° : Dial hour line angle°
 6 AM      -89.500              84.225
 7 AM      -74.500              17.283
 8 AM      -59.500               8.334
 9 AM      -44.500               4.847
10 AM      -29.500               2.795
11 AM      -14.500               1.278
12 PM        0.500              -0.043
 1 PM       15.500              -1.371
 2 PM       30.500              -2.910
 3 PM       45.500              -5.018
 4 PM       60.500              -8.671
 5 PM       75.500             -18.451
 6 PM       90.500             -95.775
```
