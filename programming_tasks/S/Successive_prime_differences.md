[1]: https://rosettacode.org/wiki/Successive_prime_differences

# [Successive prime differences][1]

```ruby
var limit  = 1e6
var primes = limit.primes
 
say "Groups of successive primes <= #{limit.commify}:"
 
for diffs in [[2], [1], [2,2], [2,4], [4,2], [6,4,2]] {
 
    var groups = []
    primes.each_cons(diffs.len+1, {|*group|
        if (group.map_cons(2, {|a,b| b-a}) == diffs) {
            groups << group
        }
    })
 
    say ("...for differences #{diffs}, there are #{groups.len} groups, where ",
         "the first group = #{groups.first} and the last group = #{groups.last}")
}
```

#### Output:
```
Groups of successive primes <= 1,000,000:
...for differences [2], there are 8169 groups, where the first group = [3, 5] and the last group = [999959, 999961]
...for differences [1], there are 1 groups, where the first group = [2, 3] and the last group = [2, 3]
...for differences [2, 2], there are 1 groups, where the first group = [3, 5, 7] and the last group = [3, 5, 7]
...for differences [2, 4], there are 1393 groups, where the first group = [5, 7, 11] and the last group = [999431, 999433, 999437]
...for differences [4, 2], there are 1444 groups, where the first group = [7, 11, 13] and the last group = [997807, 997811, 997813]
...for differences [6, 4, 2], there are 306 groups, where the first group = [31, 37, 41, 43] and the last group = [997141, 997147, 997151, 997153]
```
