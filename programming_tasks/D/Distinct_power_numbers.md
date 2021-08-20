[1]: https://rosettacode.org/wiki/Distinct_power_numbers

# [Distinct power numbers][1]

```ruby
[2..5]*2 -> cartesian.map_2d {|a,b| a**b }.sort.uniq.say
```


Alternative solution:

```ruby
2..5 ~X** 2..5 -> sort.uniq.say
```

#### Output:
```
[4, 8, 9, 16, 25, 27, 32, 64, 81, 125, 243, 256, 625, 1024, 3125]
```
