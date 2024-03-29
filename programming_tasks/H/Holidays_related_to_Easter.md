[1]: https://rosettacode.org/wiki/Holidays_related_to_Easter

# [Holidays related to Easter][1]

```ruby
require('Date::Calc')
 
var abbr = < Nil Jan Feb Mar Apr May Jun Jul Aug Sep Oct Nov Dec >
 
var holidays = [
    [Easter    => 0],
    [Ascension => 39],
    [Pentecost => 49],
    [Trinity   => 56],
    [Corpus    => 60],
]
 
func easter(year) {
    var ay = (year % 19)
    var by = (year // 100)
    var cy = (year % 100)
    var dy = (by // 4)
    var ey = (by % 4)
    var fy = ((by + 8) // 25)
    var gy = ((by - fy + 1) // 3)
    var hy = ((19*ay + by - dy - gy + 15) % 30)
    var iy = (cy // 4)
    var ky = (cy % 4)
    var ly = ((32 + 2*ey + 2*iy - hy - ky) % 7)
    var md = (hy + ly - 7*((ay + 11*hy + 22*ly) // 451) + 114)
    var month = (md // 31)
    var day = (md % 31 + 1)
    return(month, day)
}
 
func cholidays(year) {
    var (emon, eday) = easter(year)
    printf("%4s: ", year)
    say gather {
        holidays.each { |holiday|
            var (_, mo, da) = %S<Date::Calc>.Add_Delta_Days(year, emon, eday, holiday[1])
            take("#{holiday[0]}: #{'%02d' % da} #{abbr[mo]}")
        }
    }.join(', ')
}
 
for year in (400..2100 `by` 100, 2010..2020) {
    cholidays(year)
}
```
