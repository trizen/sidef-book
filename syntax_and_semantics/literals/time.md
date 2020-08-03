# Time

Represents the [UNIX Epoch time](https://en.wikipedia.org/wiki/Unix_time).

```ruby
Time()        # seconds since the Epoch to now
Time(sec)     # seconds since the Epoch to sec
```

Example:

```ruby
var t = Time()      # Time object representing current time

say t.sec           # get the number of seconds (as a Number) from object t

say Time.micro      # micro-seconds since the Epoch (as a Number)
say Time.sec        # seconds since the Epoch (as a Number)

say t.local         # Date object with local time zone
say t.gmt           # Date object with Greenwich time zone
```
