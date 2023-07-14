[1]: https://rosettacode.org/wiki/Day_of_the_week

# [Day of the week][1]

```ruby
require('Time::Local')
 
for year in (2008 .. 2121) {
    var time = %S<Time::Local>.timelocal(0,0,0,25,11,year)
    var wd = Time(time).local.wday
    if (wd == 0) {
        say "25 Dec #{year} is Sunday"
    }
}
```

#### Output:
```
25 Dec 2011 is Sunday
25 Dec 2016 is Sunday
25 Dec 2022 is Sunday
25 Dec 2033 is Sunday
25 Dec 2039 is Sunday
25 Dec 2044 is Sunday
25 Dec 2050 is Sunday
25 Dec 2061 is Sunday
25 Dec 2067 is Sunday
25 Dec 2072 is Sunday
25 Dec 2078 is Sunday
25 Dec 2089 is Sunday
25 Dec 2095 is Sunday
25 Dec 2101 is Sunday
25 Dec 2107 is Sunday
25 Dec 2112 is Sunday
25 Dec 2118 is Sunday
```
