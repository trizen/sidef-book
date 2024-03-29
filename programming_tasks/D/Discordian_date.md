[1]: https://rosettacode.org/wiki/Discordian_date

# [Discordian date][1]

```ruby
require('Time::Piece');
 
var seasons = %w(Chaos Discord Confusion Bureaucracy The\ Aftermath);
var week_days = %w(Sweetmorn Boomtime Pungenday Prickle-Prickle Setting\ Orange);
 
func ordinal (n) {
    "#{n}" + (n % 100 ~~ [11,12,13] ? 'th'
                                    : <th st nd rd th th th th th th>[n % 10])
}
 
func ddate(ymd) {
    var d = %s'Time::Piece'.strptime(ymd, '%Y-%m-%d');
    var yold = "in the YOLD #{d.year + 1166}";
 
    var day_of_year0 = d.day_of_year;
 
    if (d.is_leap_year) {
        return "St. Tib's Day, #{yold}" if ([d.mon, d.mday] == [2, 29]);
        day_of_year0-- if (day_of_year0 >= 60); # Compensate for St. Tib's Day
    }
 
    var weekday = week_days[day_of_year0 % week_days.len];
    var season = seasons[day_of_year0 / 73];
    var season_day = ordinal(day_of_year0 % 73 + 1);
 
    return "#{weekday}, the #{season_day} day of #{season} #{yold}";
}
 
%w(2010-07-22 2012-02-28 2012-02-29 2012-03-01).each { |ymd|
    say "#{ymd} is #{ddate(ymd)}"
}
```

#### Output:
```
2010-07-22 is Pungenday, the 57th day of Confusion in the YOLD 3176
2012-02-28 is Prickle-Prickle, the 59th day of Chaos in the YOLD 3178
2012-02-29 is St. Tib's Day, in the YOLD 3178
2012-03-01 is Setting Orange, the 60th day of Chaos in the YOLD 3178
```