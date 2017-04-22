[1]: http://rosettacode.org/wiki/Leap_year

# [Leap year][1]

```perl
func isleap(year) {
    if (year %% 100) {
        return (year %% 400)
    }
    return (year %% 4)
}
```


or a little bit simpler:

```perl
func isleap(year) { year %% 100 ? (year %% 400) : (year %% 4) }
```
