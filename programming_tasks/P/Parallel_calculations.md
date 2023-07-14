[1]: https://rosettacode.org/wiki/Parallel_calculations

# [Parallel calculations][1]

The code uses the *prime\_factors()* function defined in the "Prime decomposition" task.

```ruby
var nums = [1275792312878611, 12345678915808973,
            1578070919762253, 14700694496703910,];
 
var factors = nums.map {|n| prime_factors.ffork(n) }.map { .wait }
say ((nums ~Z factors)->max_by {|m| m[1][0] })
```

#### Output:
```
$ time sidef parallel.sf
[1275792312878611, [11, 7369, 15739058129]]
sidef parallel.sf  24.46s user 0.02s system 158% cpu 15.436 total
```