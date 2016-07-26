[1]: http://rosettacode.org/wiki/Five_weekends

# [Five weekends][1]

```ruby
require('DateTime');
 
var happymonths = [];
var workhardyears = [];
var longmonths = [1, 3, 5, 7, 8, 10, 12];
 
for year in (1900 .. 2100) {
   var countmonths = 0;
   longmonths.each { |month|
        var dt = %s'DateTime'.new(
            year => year,
            month => month,
            day   => 1
        );
 
        if (dt.day_of_week == 5) {
            countmonths++;
            var yearfound = dt.year;
            var monthfound = dt.month_name;
            happymonths.append(join("  ", yearfound, monthfound));
      }
   }
 
    if (countmonths == 0) {
        workhardyears.append(year);
    }
}
 
say "There are #{happymonths.len} months with 5 full weekends!";
say "The first 5 and the last 5 of them are:";
say happymonths.first(5).join("\n");
say happymonths.last(5).join("\n");
say "No long weekends in the following #{workhardyears.len} years:";
say workhardyears.join(",");
```

#### Output:
```
There are 201 months with 5 full weekends!
The first 5 and the last 5 of them are:
1901  March
1902  August
1903  May
1904  January
1904  July
2097  March
2098  August
2099  May
2100  January
2100  October
No long weekends in the following 29 years:
1900,1906,1917,1923,1928,1934,1945,1951,1956,1962,1973,1979,1984,1990,2001,2007,2012,2018,2029,2035,2040,2046,2057,2063,2068,2074,2085,2091,2096
```
