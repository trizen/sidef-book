[1]: http://rosettacode.org/wiki/Sum_of_a_series

# [Sum of a series][1]

```ruby
say (1..^1000 -> map {|i| 1 / i**2 }«+»)
```


Alternatively, using the _reduce_ method:

```ruby
say (1..^1000 -> reduce { |a,b| a + (1 / b**2) })
```

#### Output:
```
1.64393456668155980313905802382222
```
