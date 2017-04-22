[1]: http://rosettacode.org/wiki/Sorting_algorithms/Sleep_sort

# [Sorting algorithms/Sleep sort][1]

```ruby
ARGV.map{.to_i}.map{ |i|
    { Sys.sleep(i); say i }.fork
}.each{.wait}
```

#### Output:
```
% sidef test.sf 5 1 3 2 11 6 4
1
2
3
4
5
6
11
```
