[1]: https://rosettacode.org/wiki/Cheryl's_Birthday

# [Cheryl's Birthday][1]

```ruby
struct date(day, month)
 
var dates = [
    date(15, "May"),
    date(16, "May"),
    date(19, "May"),
    date(17, "June"),
    date(18, "June"),
    date(14, "July"),
    date(16, "July"),
    date(14, "August"),
    date(15, "August"),
    date(17, "August")
]
 
var filtered = dates.grep {
    dates.grep {
        dates.map{ .day }.count(.day) == 1
    }.map{ .month }.count(.month) != 1
}
 
var birthday = filtered.grep {
    filtered.map{ .day }.count(.day) == 1
}.group_by{ .month }.values.first_by { .len == 1 }[0]
 
say "Cheryl's birthday is #{birthday.month} #{birthday.day}."
```

#### Output:
```
Cheryl's birthday is July 16.
```
