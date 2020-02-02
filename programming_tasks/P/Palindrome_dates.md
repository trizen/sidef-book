[1]: https://rosettacode.org/wiki/Palindrome_dates

# [Palindrome dates][1]

```ruby
const Date = require('Time::Piece')
 
var palindates = Enumerator({ |f|
    var d = Date.strptime("2020-02-02", "%Y-%m-%d")
    loop {
        f(d) if d.strftime("%Y%m%d").is_palindrome
        d = Date.new([d.add(Date.ONE_DAY)])
    }
})
 
palindates.first(15).each { .strftime("%Y-%m-%d").say }
```

#### Output:
```
2020-02-02
2021-12-02
2030-03-02
2040-04-02
2050-05-02
2060-06-02
2070-07-02
2080-08-02
2090-09-02
2101-10-12
2110-01-12
2111-11-12
2120-02-12
2121-12-12
2130-03-12
```
