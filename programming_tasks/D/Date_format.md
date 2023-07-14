[1]: https://rosettacode.org/wiki/Date_format

# [Date format][1]

```ruby
var time = Time.local
say time.ctime
say time.strftime("%Y-%m-%d")
say time.strftime("%A, %B %d, %Y")
```

#### Output:
```
Fri Oct 17 12:57:02 2014
2014-10-17
Friday, October 17, 2014
```
