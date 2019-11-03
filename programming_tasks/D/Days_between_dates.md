[1]: https://rosettacode.org/wiki/Days_between_dates

# [Days between dates][1]

```ruby
require('Date::Calc')
 
func days_diff(a,b) {
    %S<Date::Calc>.Delta_Days(a.split('-')..., b.split('-')...)
}
 
var date1 = "1970-01-01"
var date2 = "2019-10-02"
 
say "Date 1: #{date1}"
say "Date 2: #{date2}"
 
var days = days_diff(date1, date2)
 
say "There are #{days} days between these dates"
```

#### Output:
```
Date 1: 1970-01-01
Date 2: 2019-10-02
There are 18171 days between these dates
```
