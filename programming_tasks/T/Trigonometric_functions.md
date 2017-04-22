[1]: http://rosettacode.org/wiki/Trigonometric_functions

# [Trigonometric functions][1]

```ruby
var angle_deg = 45
var angle_rad = Num.pi/4

for arr in [
    [sin(angle_rad), sin(deg2rad(angle_deg))],
    [cos(angle_rad), cos(deg2rad(angle_deg))],
    [tan(angle_rad), tan(deg2rad(angle_deg))],
    [cot(angle_rad), cot(deg2rad(angle_deg))],
] {
    say arr.join(" ")
}

for n in [
    asin(sin(angle_rad)),
    acos(cos(angle_rad)),
    atan(tan(angle_rad)),
    acot(cot(angle_rad)),
] {
    say [n, rad2deg(n)].join(' ')
}
```

#### Output:
```
0.707106781186547 0.707106781186547
0.707106781186548 0.707106781186548
1 1
1 1
0.785398163397448 45
0.785398163397448 45
0.785398163397448 45
0.785398163397448 45
```
