[1]: http://rosettacode.org/wiki/Averages/Mean_time_of_day

# [Averages/Mean time of day][1]

Using the *mean_angle()* function from: ["Averages/Mean angle"](http://rosettacode.org/wiki/Averages/Mean_angle#Sidef)

```ruby
func time2deg(t) {
  t ~~ /^(\d\d):(\d\d):(\d\d)$/ || die "invalid time";
  var (hh,mm,ss) = [$1, $2, $3].map{.to_i}...;
  ((hh ~~ 0...23) && (mm ~~ 0...59) && (ss ~~ 0...59)) || die "invalid time";
  (hh*3600 + mm*60 + ss) * 360 / 86400;
}
 
func deg2time(d) {
  var sec = ((d % 360) * 86400 / 360);
  "%02d:%02d:%02d" % [sec/3600, (sec%3600)/60, sec%60];
}
 
func mean_time(times) {
  deg2time(mean_angle(times.map {|t| time2deg(t)}));
}
 
say mean_time(["23:00:17", "23:40:20", "00:12:45", "00:17:19"]);
```

#### Output:
```
23:47:43
```