[1]: http://rosettacode.org/wiki/Equilibrium_index

# [Equilibrium index][1]

```ruby
func eq_index(nums) {
    var (i, sum, sums) = (0, 0, Hash.new);
    nums.each { |n|
        sums{2*sum + n} := [] -> append(i++);
        sum += n;
    };
    sums{sum} \\ [];
}
```


Test:

```ruby
var indices = [
  [-7, 1, 5, 2,-4, 3, 0],
  [2, 4, 6],
  [2, 9, 2],
  [1,-1, 1,-1, 1,-1, 1],
]
 
indices.each { |x|
    say ("%s => %s" % @[x, eq_index(x)].map{.dump});
}
```

#### Output:
```
[-7, 1, 5, 2, -4, 3, 0] => [3, 6]
[2, 4, 6] => []
[2, 9, 2] => [1]
[1, -1, 1, -1, 1, -1, 1] => [0, 1, 2, 3, 4, 5, 6]
```