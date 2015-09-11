[1]: http://rosettacode.org/wiki/Trigonometric_functions

# [Trigonometric functions][1]

```ruby
var angle_deg = 45;
var angle_rad = Math.pi/4;
 
[
    [Math.sin(angle_rad), Math.sin(Math.deg2rad(angle_deg))],
    [Math.cos(angle_rad), Math.cos(Math.deg2rad(angle_deg))],
    [Math.tan(angle_rad), Math.tan(Math.deg2rad(angle_deg))],
    [Math.cot(angle_rad), Math.cot(Math.deg2rad(angle_deg))],
].each { |arr|
    say arr.join(" ");
}
 
[
    Math.asin(Math.sin(angle_rad)),
    Math.acos(Math.cos(angle_rad)),
    Math.atan(Math.tan(angle_rad)),
    Math.acot(Math.cot(angle_rad)),
].each { |n|
    say [n, Math.rad2deg(n)].join(" ");
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