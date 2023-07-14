[1]: https://rosettacode.org/wiki/Trabb_Pardo–Knuth_algorithm

# [Trabb Pardo–Knuth algorithm][1]

```ruby
var nums; do {
    nums = Sys.readln("Please type 11 space-separated numbers: ").nums
} while(nums.len != 11)
 
nums.reverse.each { |n|
    var r = (n.abs.sqrt + (5 * n**3))
    say "#{n}\t#{ r > 400 ? 'Urk!' : r }"
}
```

#### Output:
```
Please type 11 space-separated numbers: 10 -1 1 2 3 4 4.3 4.305 4.303 4.302 4.301
4.301   399.886299747726800445468371077898575778355
4.302   Urk!
4.303   Urk!
4.305   Urk!
4.3     399.608644135332772087455898679984992632401
4       322
3       136.732050807568877293527446341505872366943
2       41.41421356237309504880168872420969807857
1       6
-1      -4
10      Urk!
```
