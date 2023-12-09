[1]: https://rosettacode.org/wiki/Sum_of_a_series

# [Sum of a series][1]

```ruby
say sum(1..1000, {|n| 1 / n**2 })
```


Alternatively, using the _reduce{}_ method:

```ruby
say (1..1000 -> reduce { |a,b| a + (1 / b**2) })
```

#### Output:
```
1.64393456668155980313905802382221558965210344649
```
