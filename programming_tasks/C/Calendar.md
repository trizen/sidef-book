[1]: http://rosettacode.org/wiki/Calendar

# [Calendar][1]

```ruby
require('DateTime')

define months_per_col = 3
define week_day_names = <Mo Tu We Th Fr Sa Su>
define month_names = <Jan Feb Mar Apr May Jun Jul Aug Sep Oct Nov Dec>

func fmt_month (year, month) {
    var str = sprintf("%-20s\n", month_names[month-1])
    str += week_day_names.join(' ')+"\n"

    var dt = %s'DateTime'
    var date = dt.new(year => year, month => month)
    var week_day = date.day_of_week
    str += (["  "] * week_day-1 -> join(" "))

    var last_day = dt.last_day_of_month(year => year, month => month).day
    for day in range(date.day, last_day) {
        date = dt.new(year => year, month => month, day => day)

        str += " " if (week_day ~~ range(2,7))
        if (week_day == 8) {
            str += "\n"
            week_day = 1
        }
        str += sprintf("%2d", day)
        ++week_day
    }
    str += " " if (week_day < 8)
    str += (["  "] * 8-week_day -> join(" "))
    str += "\n"
}

func fmt_year (year) {
    var month_strs = 12.of { |i| fmt_month(year, i).lines }

    var str = (' '*30 + year + "\n")
    for month in range(0, 11, months_per_col) {
        while (month_strs[month]) {
            months_per_col.times { |i|
                month_strs[month + i - 1] || next
                str += month_strs[month + i - 1].shift
                str += ' '*3
            }
            str += "\n"
        }
        str += "\n"
    }

    return str
}

print fmt_year(ARGV.is_empty ? 1969 : ARGV[0].to_i)
```

#### Output:
```
                              1969
Jan                    Feb                    Mar
Mo Tu We Th Fr Sa Su   Mo Tu We Th Fr Sa Su   Mo Tu We Th Fr Sa Su
       1  2  3  4  5                   1  2                   1  2
 6  7  8  9 10 11 12    3  4  5  6  7  8  9    3  4  5  6  7  8  9
13 14 15 16 17 18 19   10 11 12 13 14 15 16   10 11 12 13 14 15 16
20 21 22 23 24 25 26   17 18 19 20 21 22 23   17 18 19 20 21 22 23
27 28 29 30 31         24 25 26 27 28         24 25 26 27 28 29 30

Apr                    May                    Jun
Mo Tu We Th Fr Sa Su   Mo Tu We Th Fr Sa Su   Mo Tu We Th Fr Sa Su
    1  2  3  4  5  6             1  2  3  4                      1
 7  8  9 10 11 12 13    5  6  7  8  9 10 11    2  3  4  5  6  7  8
14 15 16 17 18 19 20   12 13 14 15 16 17 18    9 10 11 12 13 14 15
21 22 23 24 25 26 27   19 20 21 22 23 24 25   16 17 18 19 20 21 22
28 29 30               26 27 28 29 30 31      23 24 25 26 27 28 29

Jul                    Aug                    Sep
Mo Tu We Th Fr Sa Su   Mo Tu We Th Fr Sa Su   Mo Tu We Th Fr Sa Su
    1  2  3  4  5  6                1  2  3    1  2  3  4  5  6  7
 7  8  9 10 11 12 13    4  5  6  7  8  9 10    8  9 10 11 12 13 14
14 15 16 17 18 19 20   11 12 13 14 15 16 17   15 16 17 18 19 20 21
21 22 23 24 25 26 27   18 19 20 21 22 23 24   22 23 24 25 26 27 28
28 29 30 31            25 26 27 28 29 30 31   29 30

Oct                    Nov                    Dec
Mo Tu We Th Fr Sa Su   Mo Tu We Th Fr Sa Su   Mo Tu We Th Fr Sa Su
       1  2  3  4  5                   1  2    1  2  3  4  5  6  7
 6  7  8  9 10 11 12    3  4  5  6  7  8  9    8  9 10 11 12 13 14
13 14 15 16 17 18 19   10 11 12 13 14 15 16   15 16 17 18 19 20 21
20 21 22 23 24 25 26   17 18 19 20 21 22 23   22 23 24 25 26 27 28
27 28 29 30 31         24 25 26 27 28 29 30   29 30 31
```
