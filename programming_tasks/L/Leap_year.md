[1]: http://rosettacode.org/wiki/Leap_year

# [Leap year][1]

```ruby
func isleap(year) {
    if (year % 100 == 0) {
        return (year % 400 == 0);
    };
    return (year % 4 == 0);
}
```


or a little bit simpler:

```ruby
func isleap(year) { 100.divides(year) ? 400.divides(year) : 4.divides(year) };
```
