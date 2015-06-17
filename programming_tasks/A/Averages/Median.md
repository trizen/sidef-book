[1]: http://rosettacode.org/wiki/Averages/Median

# [Averages/Median][1]

```ruby
func median(arry) {
    var srtd = arry.sort;
    var alen = srtd.length;
    srtd[(alen-1)/2]+srtd[alen/2] / 2;
}
```