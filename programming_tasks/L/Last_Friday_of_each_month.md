[1]: http://rosettacode.org/wiki/Last_Friday_of_each_month

# [Last Friday of each month][1]

```ruby
require('DateTime');
var (year=2015) = ARGV»to_i»()...;
 
range(1, 12).each { |month|
   var dt = %s'DateTime'.last_day_of_month(year => year, month => month);
   while (dt.day_of_week != 5) {
      dt.subtract(days => 1);
   };
   say dt.ymd;
}
```

#### Output:
```
$ sidef lastfriday.sf 2012
2012-01-27
2012-02-24
2012-03-30
2012-04-27
2012-05-25
2012-06-29
2012-07-27
2012-08-31
2012-09-28
2012-10-26
2012-11-30
2012-12-28
```
