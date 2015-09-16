[1]: http://rosettacode.org/wiki/Permutations_by_swapping

# [Permutations by swapping][1]

```ruby
func perms(xx) {
   var perms = [[+1]];
   range(1, xx).each { |x|
      var sign = -1;
      perms.flat_map! { |arr|
          var (s, *p) = arr...;
          var r = range(0, p.len);
          (s < 0 ? r : r.reverse).map {|i|
            [sign *= -1, p[0..i-1]..., x, p[i..p.end]...]
          };
      }
   };
   perms;
}
 
var n = 4;
perms(n).each { |p|
    var s = p.shift;
    s > 0 && (s = '+1');
    say "#{p.dump} => #{s}";
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