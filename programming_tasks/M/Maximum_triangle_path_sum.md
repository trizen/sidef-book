[1]: https://rosettacode.org/wiki/Maximum_triangle_path_sum

# [Maximum triangle path sum][1]

Iterative solution:

```ruby
var sum = [0]

ARGF.each {  |line|
    var x = line.words.map{.to_n}
    sum = [
            x.first + sum.first,
            {|i| x[i] + [sum[i-1, i]].max }.map(1 ..^ x.end)...
            x.last + sum.last,
          ]
}

say sum.max
```


Recursive solution:

```ruby
var triangle = ARGF.slurp.lines.map{.words.map{.to_n}}
 
func max_value(i=0, j=0) is cached {
    i == triangle.len && return 0
    triangle[i][j] + [max_value(i+1, j), max_value(i+1, j+1)].max
}
 
say max_value()
```

#### Output:
```
% sidef maxpath.sf triangle.txt
1320
```
