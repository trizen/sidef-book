[1]: http://rosettacode.org/wiki/Ordered_Partitions

# [Ordered Partitions][1]

```ruby
func part(_,    {.is_empty}) { [[]] }
func partitions({.is_empty}) { [[]] }
 
func part(s, args) {
  var res = [];
  var combs = s.combinations(args[0]);
  combs << [] if combs.is_empty;
  combs.each { |c|
    part(s - c, args.ft(1)).each{|r| res << ([c] + r)}
  }
  res
}
 
func partitions(args) {
  part(1..args.sum, args)
}
 
[[],[0,0,0],[1,1,1],[2,0,2]].each { |test_case|
  say "partitions #{test_case.dump}:"
  partitions(test_case).each{|part| say part.dump }
  print "\n"
}
```

#### Output:
```
partitions []:
[]

partitions [0, 0, 0]:
[[], [], []]

partitions [1, 1, 1]:
[[1], [2], [3]]
[[1], [3], [2]]
[[2], [1], [3]]
[[2], [3], [1]]
[[3], [1], [2]]
[[3], [2], [1]]

partitions [2, 0, 2]:
[[1, 2], [], [3, 4]]
[[1, 3], [], [2, 4]]
[[1, 4], [], [2, 3]]
[[2, 3], [], [1, 4]]
[[2, 4], [], [1, 3]]
[[3, 4], [], [1, 2]]
```