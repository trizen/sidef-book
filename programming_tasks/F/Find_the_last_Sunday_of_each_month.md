[1]: http://rosettacode.org/wiki/Find_the_last_Sunday_of_each_month

# [Find the last Sunday of each month][1]

```ruby
var dt = require('DateTime')
var (year=2016) = ARGV.map{.to_i}...

for i in (1 .. 12) {
    var date = dt.last_day_of_month(
        year  => year,
        month => i
    )

    while (date.dow != 7) {
        date = date.subtract(days => 1)
    }

    say date.ymd
}
```

#### Output:
```
$ sidef last_sunday.sf 2013
2013-01-27
2013-02-24
2013-03-31
2013-04-28
2013-05-26
2013-06-30
2013-07-28
2013-08-25
2013-09-29
2013-10-27
2013-11-24
2013-12-29
```
