[1]: https://rosettacode.org/wiki/Permutations_by_swapping

# [Permutations by swapping][1]

```ruby
func perms(n) {
   var perms = [[+1]]
   for x in (1..n) {
      var sign = -1
      perms = gather {
        for s,*p in perms {
          var r = (0 .. p.len)
          take((s < 0 ? r : r.flip).map {|i|
            [sign *= -1, p[^i], x, p[i..p.end]]
          }...)
        }
      }
   }
   perms
}

var n = 4
for p in perms(n) {
    var s = p.shift
    s > 0 && (s = '+1')
    say "#{p} => #{s}"
}
```

#### Output:
```
[1, 2, 3, 4] => +1
[1, 2, 4, 3] => -1
[1, 4, 2, 3] => +1
[4, 1, 2, 3] => -1
[4, 1, 3, 2] => +1
[1, 4, 3, 2] => -1
[1, 3, 4, 2] => +1
[1, 3, 2, 4] => -1
[3, 1, 2, 4] => +1
[3, 1, 4, 2] => -1
[3, 4, 1, 2] => +1
[4, 3, 1, 2] => -1
[4, 3, 2, 1] => +1
[3, 4, 2, 1] => -1
[3, 2, 4, 1] => +1
[3, 2, 1, 4] => -1
[2, 3, 1, 4] => +1
[2, 3, 4, 1] => -1
[2, 4, 3, 1] => +1
[4, 2, 3, 1] => -1
[4, 2, 1, 3] => +1
[2, 4, 1, 3] => -1
[2, 1, 4, 3] => +1
[2, 1, 3, 4] => -1
```
