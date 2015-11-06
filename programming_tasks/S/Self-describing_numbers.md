[1]: http://rosettacode.org/wiki/Self-describing_numbers

# [Self-describing numbers][1]

```ruby
func sdn(n) {
    var b = [0]*n.len;
    var a = n.digits;
    a.each { |i| b[i] := 0 ++ }
    a.join == b.join;
}
 
var values = %n(1210 2020 21200 3211000
42101000 521001000 6210001000 27 115508);
 
values.each { |test|
    say "#{test} is #{sdn(test) ? '' : 'NOT ' }a self describing number.";
}
 
range(0, 1e5).each { |i say i if sdn(i) }
```

#### Output:
```
1210 is a self describing number.
2020 is a self describing number.
21200 is a self describing number.
3211000 is a self describing number.
42101000 is a self describing number.
521001000 is a self describing number.
6210001000 is a self describing number.
27 is NOT a self describing number.
115508 is NOT a self describing number.
1210
2020
21200
^C
```