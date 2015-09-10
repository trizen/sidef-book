[1]: http://rosettacode.org/wiki/Date_manipulation

# [Date manipulation][1]

```ruby
var dt = frequire('DateTime::Format::Strptime');
 
var input =  'March 7 2009 7:30pm EST';
input.sub!('EST', 'America/New_York');
 
say dt.strptime('%b %d %Y %I:%M%p %O', input).
        add(hours => 12).
        set_time_zone('America/Edmonton').
        format_cldr('MMMM d yyyy h:mma zzz');
```

#### Output:
```
March 8 2009 6:30AM MDT
```