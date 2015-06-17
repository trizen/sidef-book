[1]: http://rosettacode.org/wiki/Maximum_triangle_path_sum

# [Maximum triangle path sum][1]

```ruby
var sum = [0];
 
ARGF.each {  |line|
    var x = line.words.map{.to_i};
    sum = [
            x.first + sum.first,
            1 .. x.len-2 -> map{|i| x[i] + sum[i-1, i].max}...,
            x.last + sum.last,
        ];
}
 
say sum.max;
```

#### Output:
```
% sidef maxpath.sf triangle.txt
1320
```