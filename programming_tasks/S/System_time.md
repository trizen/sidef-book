[1]: https://rosettacode.org/wiki/System_time

# [System time][1]

```ruby
# textual
say Time.local.ctime         # => Thu Mar 19 15:10:41 2015
 
# epoch time
say Time.sec                 # => 1426770641
 
# epoch time with fractional seconds
say Time.micro_sec           # => 1426770641.68409
```
